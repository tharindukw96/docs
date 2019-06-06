---
toc: true
title: Auth0 Deprecations
description: List of all the deprecations in progress
topics:
  - deprecations
  - migrations
contentType:
  - concept
  - reference
useCase:
  - migrate
---

# Deprecations

In an effort to keep the Auth0 platform stable and secure some features must occasionally be removed from service.

This proccess starts with the feature being **Deprecated**. Our policy provides at least a six month grace period before the **Removal Date**, at which point using the deprecated functionality will result in an error. Depending on the severity of the issue the grace period time frame may be accelerated.

Typcially there will be a replacement for the feature being removed (e.g. new version of an API or SDK, alternative API endpoint, etc.). While we make our best effort to maintain backward compatibility, the replacement will often result in a breaking change or require a migration to a new version. In that case a migration guide will be provided to help ensure you're fully prepared for the.

<table class="table">
  <thead>
    <tr>
      <th style="width: 156px;">Feature</th>
      <th style="width: 100px;">Deprecated</th>
      <th style="width: 233px;">Removal Date</th>
      <th>Details</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><a href="/users/search/v3/migrate-search-v2-v3">User Search v2</a></td>
      <td>6 June 2018</td>
      <td>30 June 2019</td>
      <td>User Search v2 is being deprecated and you may be required to take action before June 30, 2019. A <a href="/users/search/v3/migrate-search-v2-v3">migration guide</a> is available to walk you through the steps required. Notifications have been and will continue to be sent to customers that need to complete this migration.<br>Useful Resources:<br>
        <a href="/users/search/v3">User Search v3</a><br>
        <a href="/users/search/v3/query-syntax">User Search v3 - Query Syntax</a><br>
        <a href="/best-practices/search-best-practices">User Search Best Practices</a><br>
        <a href="/users/search/v3/migrate-search-v2-v3">User Search v2 to v3 Migration Guide</a><br>
      </td>
    </tr>
    <tr>
      <td><a href="/logs/migrate-logs-v2-v3">Tenant Logs Search v2</a></td>
      <td>21 May 2019</td>
      <td>
        <b>Free</b>: 15 June 2019<br>
        <b>Developer</b>: 20 August 2019<br>
        <b>Developer Pro</b>: 20 August 2019<br>
        <b>Enterprise</b>: 4 November 2019
      </td>
      <td>To provide our customers with the most reliable and scalable solution, Auth0 has deprecated Tenant Logs Search Engine v2 in favor of v3. Auth0 is proactively migrating customers unaffected by this change, while those who are potentially affected are being notified to opt in for v3 during the provided grace period.  See the <a href="/logs/migrate-logs-v2-v3">migration guide</a> for more information.</td>
    </tr>
    <tr>
      <td><a href="/migrations/guides/extensibility-node8">Node.js v4 Extensibility Runtime</a></td>
      <td>17 April 2019</td>
      <td>30 June 2019</td>
      <td>
        The Webtask engine powering Auth0 extensibility points currently utilizes Node 4. Beginning <strong>30 April 2018</strong>, <a href="https://github.com/nodejs/Release#release-schedule">Node.js v4 will no longer be under long-term support (LTS)</a>. This means that critical security fixes will no longer be back-ported to this version. As such, Auth0 will be migrating the Webtask runtime from Node.js v4 to Node.js v8.<br><br>On <strong>17 April 2018</strong> we will make the Node 8 runtime available for extensibility to all public cloud customers. You will be provided a migration switch that allows you to control your environment's migration to the new runtime environment.<br><br>For more information on this migration and the steps you should follow to upgrade your implementation, see <a href="/migrations/guides/extensibility-node8">Migration Guide: Extensibility and Node.js v8</a>.
      </td>
    </tr>
  </tbody>
</table>

## Planned deprecations

Based on customer feedback, we have adjusted our plans and will continue to maintain and support the below listed endpoints and features.

We will publish guidance for each of the below scenarios on how to transition your applications to standards-based protocols. If we need to make security enhancements to any of these legacy endpoints which would require more urgency, we will promptly announce timeframes and guidelines for any required changes.

### Allow ID Tokens for Management API v2 Authentication

For some use cases you can use [ID Tokens](/tokens/id-token) as credentials in order to call the [Management API](/api/management/v2).

The functionality is available and affected users are encouraged to migrate. However the ability to use ID Tokens will not be disabled in the foreseeable future so the mandatory opt-in date for this migration remains open. When this changes, customers will be notified beforehand.

For more information on this migration and the steps you should follow to upgrade your implementation, see the [Migration Guide: Management API and ID Tokens](/migrations/guides/calling-api-with-idtokens).

#### Am I affected by the change?

If you are currently using [ID Tokens](/tokens/id-token) to access any part of the Management API, your application will need to be updated.

### Legacy oauth/ro Endpoint

Support was introduced for [Resource Owner Password](/api/authentication#resource-owner-password) to the [/oauth/token](/api/authentication#authorization-code) endpoint earlier this year.

#### Am I affected by the change?

If you are currently implementing the [/oauth/ro](/api/authentication#resource-owner) endpoint your application can be updated to use the [/oauth/token](/api/authentication#authorization-code) endpoint. For details on how to make this transition, see the [Migration Guide for Resource Owner Password Credentials Exchange](/migrations/guides/migration-oauthro-oauthtoken).

If you have any questions, create a ticket in our [Support Center](${env.DOMAIN_URL_SUPPORT}).

### Legacy Delegation Endpoint (API authorization with third-party vendor APIs)

The mechanism by which you get tokens for third-party / vendor APIs (for example AWS, Firebase, and others) is being changed. It will work the same as any custom API, providing better consistency. This new architecture will be available in 2019 and once it becomes available, the [/delegation](/api/authentication#delegation) endpoint will be officially deprecated.

#### Am I affected by the change?

If you are currently using [/delegation](/api/authentication#delegation) to provide third party authorization, your application will need to be updated once migration guides are available.

If you have any questions, create a ticket in our [Support Center](${env.DOMAIN_URL_SUPPORT}).

### Legacy User Profile

The [userinfo](/api/authentication#get-user-info) endpoint is being updated to return [OIDC conformant user profile attributes](/users/normalized/oidc). The most notable change is that `user_id` becomes `sub`. This will deprecate the [legacy Auth0 user profile](/users/normalized/auth0) (in [userinfo](/api/authentication#get-user-info) and in [ID Tokens](/tokens/id-token)).

#### Am I affected by the change?

If you are currently using the [/userinfo](/api/authentication#get-user-info) endpoint or receiving ID Tokens, you are affected by this change and need to update your implementation so that it expects normalized OIDC conformant user profile attributes once migration guides are available.

If you have any questions, create a ticket in our [Support Center](${env.DOMAIN_URL_SUPPORT}).