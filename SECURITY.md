# Security Policy

## Reporting a Vulnerability

Please report any potential security issues to `<open-horizon-security@lists.lfedge.org>`. This will notify the core project team who will respond accordingly.

## CVE History

- On November 1 2022, the OpenSSL community released [OpenSSL 3.0.7](https://www.openssl.org/news/openssl-3.0-notes.html) which detailed two vulnerability alerts; [CVE-2022-3786](https://www.openssl.org/news/vulnerabilities.html#CVE-2022-3786) and [CVE-2022-3602](https://www.openssl.org/news/vulnerabilities.html#CVE-2022-3602). Both high severity CVE alerts related to x.509 certificate verification buffer overruns.
  - Open Horizon is not affected by these CVE security alerts
    - Open Horizon uses TLS encryption in the anax / exchange / css / vault / SDO components via the **Go** [crypto/tls](https://pkg.go.dev/crypto/tls) library.
    - Several Open Horizon components use the OpenSSL 1.x command line utilities to generate x.509 certificates / keys within containers and for testing.
    - Only the Open Horizon Exchange UBI9 based container includes the OpenSSL 3.0.x package to generate x.509 certificates. This usage is not affected by the CVE alerts resolved by OpenSSL 3.0.7
    - In the abundance of caution, the Exchange UBI9 container with the recently released OpenSSL 3.0.7 package will be rebuilt.  That work is being tracked by [Exchange API Issue #650](https://github.com/open-horizon/exchange-api/issues/650)

[comment]: <>    - Open Horizon users can upgrade by pulling v2.87.4+ from the latest released branch or anything v2.102.0+ from the master branch.
