---
title: Overview
description: Casdoor basic unit — organization
keywords: [organization]
authors: [sh1luo]
---

An organization is the basic unit of Casdoor, which manages users and applications. If a user signs in to an organization, then they can access all applications belonging to the organization without signing in again.

In the configuration of [applications](/docs/application/config) and [providers](/docs/provider/overview), choosing an organization is important, as it determines whether a user can access the application using specific providers.

We can also set up LDAP in Casdoor. For more details, please see the [LDAP](/docs/ldap/overview) documentation.

Casdoor provides multiple password storage algorithms that can be selected on the organization edit page.

|Name|Algorithm|Description|Scenario|
|:--:|:--:|--|:--:|
|plain|-|The password will be stored in cleartext. (default)|-|
|salt|[SHA-256](https://github.com/casdoor/casdoor/blob/master/cred/sha256-salt.go)|[SHA-256](https://www.n-able.com/blog/sha-256-encryption) is a patented cryptographic hash function that outputs a value that is 256 bits long.|-|
|md5-salt|[MD5](https://github.com/casdoor/casdoor/blob/master/cred/md5-user-salt.go)|The [MD5 message-digest algorithm](https://en.wikipedia.org/wiki/MD5) is a cryptographically broken but still widely used hash function producing a 128-bit hash value. |[Discuz!](https://www.discuz.net/)|
|bcrypt|[bcrypt](https://github.com/casdoor/casdoor/blob/master/cred/bcrypt.go)|[bcrypt](https://en.wikipedia.org/wiki/Bcrypt) is a password-hashing function and is used to hash and salt passwords securely.|[Spring Boot](https://spring.io/projects/spring-boot), [WordPress](https://stackoverflow.com/questions/1045988/what-type-of-hash-does-wordpress-use)|
|pbkdf2-salt|[SHA-256 and PBKDF2](https://github.com/casdoor/casdoor/blob/master/cred/pbkdf2-salt.go)|[PBKDF2](https://en.wikipedia.org/wiki/PBKDF2) is a simple cryptographic key derivation function that is resistant to dictionary attacks and rainbow table attacks. It was originally implemented in Casdoor for the Keycloak syncer. Select this option if you are importing users using the Keycloak syncer.|[Keycloak](http://keycloak.org/)|

:::tip

In addition to logging into Casdoor via an application (which redirects to Casdoor for SSO), a Casdoor user can also choose to directly log into Casdoor via the organization's login page: `/login/<organization_name>`, e.g., <https://door.casdoor.com/login/casbin> in the demo site.

:::
