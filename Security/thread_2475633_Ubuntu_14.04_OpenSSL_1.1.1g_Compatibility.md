---
title: "Ubuntu 14.04: OpenSSL 1.1.1g Compatibility"
date: 2022-06-02
forum: Security
---

### Post by anshah on 2022-06-02
Is Open SSL Version 1.1.1g compatible with Ubuntu 14.04? 
I was able to build and generate the library files with no issues but I saw failures when I ran "make test."

```
Test Summary Report
-------------------
../test/recipes/80-test_ssl_new.t                (Wstat: 256 Tests: 29 Failed: 1)
  Failed test:  12
  Non-zero exit status: 1
Files=155, Tests=1468, 87 wallclock secs ( 1.76 usr  0.24 sys + 63.36 cusr  5.11 csys = 70.47 CPU)
Result: FAIL
make[1]: *** [_tests] Error 1
make[1]: Leaving directory `/home/anshah/Downloads/openssl-1.1.1g'
make: *** [tests] Error 2



```

---

### Post by ajgreeny on 2022-06-02
We are unable to help you with this query.

Ubuntu 14.04 has been EOL and out of support for over 3 years now and should not be used, certainly never online as it would be far too risky not just for you but for the whole community.

Please install a fully supported version and we will help if we're able, though it will then, of course. have absolutely nothing to do with 14.04.

---

