# Introduction

The Risban API is organized around REST. Our API has predictable resource-oriented URLs, accepts form-encoded request bodies, returns JSON-encoded responses, and uses standard HTTP response codes, authentication, and verbs.

You can use the Risban API in test mode, which does not affect your live data or interact with the banking networks. The API key you use to authenticate the request determines whether the request is live mode or test mode.

## Authentication

The Risban API uses API keys to authenticate requests. You can view and manage your API keys in the Risban Dashboard.

Test mode secret keys have the prefix `rb_test_` and live mode secret keys have the prefix `rb_live_`. Alternatively, you can use restricted API keys for granular permissions.

Your API keys carry many privileges, so be sure to keep them secure! Do not share your secret API keys in publicly accessible areas such as GitHub, client-side code, and so forth.

Authentication to the API is performed via HTTP Basic Auth. Provide your API key as the basic auth username value. You do not need to provide a password.

If you need to authenticate via bearer auth (e.g., for a cross-origin request), use `-H "Authorization: Bearer rb_test_4eC39HqLyjWDarjtT1zdp7dc"` instead of `-u rb_test_4eC39HqLyjWDarjtT1zdp7dc`.

All API requests must be made over HTTPS. Calls made over plain HTTP will fail. API requests without authentication will also fail.

## Errors

Risban uses conventional HTTP response codes to indicate the success or failure of an API request. In general: Codes in the 2xx range indicate success. Codes in the 4xx range indicate an error that failed given the information provided (e.g., a required parameter was omitted, a charge failed, etc.). Codes in the 5xx range indicate an error with Risban's servers (these are rare).

Some 4xx errors that could be handled programmatically (e.g., a card is declined) include an error code that briefly explains the error reported.

<!-- title: HTTP Status Codes -->

| Code |     Text      |  Description                           |
| -----| :-----------: | -------------------------------------: |
| 200  | OK            | Success!                               |
| 202  | Accepted   | Accepted by us, but processing is not yet complete                                                        |
| 304 | Not Modified   |    There was no new data to return.    |
| 400 | Bad Request | The request was invalid or cannot be otherwise served. An accompanying error message will explain further. Requests without authentication are considered invalid and will yield this response.                                   | 
|401 | Unauthorized	| Missing or incorrect authentication credentials.                                                    |
|403	| Forbidden	| The request is understood, but it has been refused or access is not allowed. An accompanying error message will explain why.                                               |
| 404	| Not Found	| The URI requested is invalid or the resource requested, such as a user, does not exist. Also returned when the requested format is not supported by the requested method.      |
| 410	| Gone	| This resource is gone. Used to indicate that an API endpoint has been turned off.                               |
| 429	| Too Many Requests	| Returned when a request cannot be served due to rate limiting                                     |
| 500	| Internal Server Error	| Something is broken. Please post to the developer forums with additional details of your request, so the Railsbank team can investigate.                          |
| 502	| Bad Gateway	| Railsbank is down or being upgraded.      |
| 503	| Service Unavailable	| The Railsbank servers are up, but overloaded with requests. Try again later.                      |
| 504	| Gateway timeout	| The Railsbank servers are up, but the request couldn’t be serviced due to some failure within our stack. Try again later.                                         |

> A primary goal of Studio is to enrich, not replace, your existing workflows. It works offline, with folders and files on your computer, just like your favorite IDEs.

Read the full [Studio Docs](https://stoplight.io/p/docs/gh/stoplightio/studio).

Here is some of what it can do:

- **OpenAPI v2 and v3:** Form based design mode means you don't need to be an OpenAPI expert to get started. Studio also supports OpenAPI autocomplete in write mode, a read mode to visualize HTTP operations and models, mocking, and linting for OpenAPI v2 and v3.
- **Standalone JSON Schema Modeling:** Studio encourages you to split your models into separate files, and then makes it easy to create `$refs` between them.
- **Stoplight Flavored Markdown:** [SMD](./markdown/stoplight-flavored-markdown.md) is an optional, lightweight extension to regular markdown. It enables a few advanced features such as tabs and callouts.
- **Combine Reference and Implementation:** Since Studio works with your local filesystem, you can open up your API projects and start adding docs and designs alongside the actual implementation they are meant to describe. Once you're done, check it all into git with your favorite git client!
- **Manage Mock Servers:** Studio automatically starts local mock servers for every API defined in your project, and keeps those mock servers up to date as you change your designs.

## A Note on this Personal Space

This initial Studio project template was cloned from the [Studio Templates](https://github.com/stoplightio/studio-templates) Github repository. If you find an error, or have an idea on how to improve this getting started template, please let us know in the issues section of that repository.

We plan to add additional sections on Prism (mocking), Spectral (linting), working with the filesystem, Git, and more in the future.

This template includes a couple of example APIs (Petstore and To-dos). You can create a new project, or open another folder on your computer, by clicking the `Project Selector` dropdown in the top left of the Studio UI.