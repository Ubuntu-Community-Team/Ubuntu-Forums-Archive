---
title: "Why aptly said &quot;gpg: no default secret key: secret key not available&quot; when GPG works?"
date: 2022-10-02
forum: Security
---

### Post by fradobhalla on 2022-10-02
Why aptly said "gpg: no default secret key: secret key not available" when GPG works?

```
frado8@comp:/home/frado/work/co/product_g$ export DEBEMAIL=fbhalla@company.net
frado8@comp:/home/frado/work/co/product_g$ export DEBFULLNAME='Frado Bhalla'
frado8@comp:/home/frado/work/co/product_g$ echo $DEBEMAIL
fbhalla@company.net
frado8@comp:/home/frado/work/co/product_g$ echo $DEBFULLNAME
Frado Bhalla
frado8@comp:/home/frado/work/co/product_g$ gpg -K
/home/frado8/.gnupg/pubring.gpg
-------------------------------
sec   rsa3072 2022-09-28 [SC]
      0FA2D236135EA1B5849E4B6306CA7B9D3DB2353D
uid           [ unknown] Bhalla Frado <fbhalla@company.net>
ssb   rsa3072 2022-09-28 [E]

frado8@comp:/home/frado/work/co/product_g$ gpg --list-keys --keyring secring.gpg
/home/frado8/.gnupg/pubring.gpg
-------------------------------
pub   rsa3072 2022-09-28 [SC]
      0FA2D236135EA1B5849E4B6306CA7B9D3DB2353D
uid           [ unknown] Bhalla Frado <fbhalla@company.net>
sub   rsa3072 2022-09-28 [E]

frado8@comp:/home/frado/work/co/product_g$ echo test | gpg --clearsign
gpg: using "fbhalla@company.net" as default secret key for signing
-----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA512

test
-----BEGIN PGP SIGNATURE-----

iQHHBAEBCgAxFiEED6LSNhNeobWEnktjBsp7nT2yNT0FAmM4uwUTHGVpdmFub3Zh
QGxhYjUwLm5ldAAKCRAGynudPbI1PSOLC/90ONQwSumVw5tfzKee4mX0GHHZ4OIf
CuGDj4J6GqEzc5I9pU/ABlFzpmQgfxUgdNSTlSBnAH51uPtUTzrVhgSumLaflKLq
fFnt10XBmQycamGXkX+0Eu8YrohDkSN8zysTND0qGMiXd8a9uh8bMzz1g5+pf6HQ
LSNzeVL8wakamgpEnU5yUbI59hj1O8/gprF2S0qXq37PiWwOj2uZn3nUyuTO8q/Q
TSXyKtSYs7qjvw3jy8LUdLM8hWi2sZNse09p5ksQNvylDVB2ZUQ5BBhk8812esSb
WBq+ifR4DMaHRR91THpzJEGDIw6XLfso65VV/AFiilw+34HAdGbmJ2M0KOcxJeQd
BBGlvkmRlOgJzFt9KAep2MV8myybeyS2bTAwHspYbnj2h8zAxDgnGwRddApzyuNu
ot+O8LjUXzkvBOMVyAIVFFE3nFoTGwzpAGXoEXfmPmrTuyOkvlOLNmJWSQAda53/
HQNdmabJwHSyxlh0Glo8k4DxEUWIlKNYY4Q=
=O+Tw
-----END PGP SIGNATURE-----
frado8@comp:/home/frado/work/co/product_g$ /home/frado/work/co/cui/cui/lbp-auto -b bundle.yml world bullseye
/home/frado/work/co/cui/cui/cui/program.py:86: YAMLLoadWarning: calling yaml.load() without Loader=... is deprecated, as the default Loader is unsafe. Please read https://msg.pyyaml.org/load for full details.
  options.update(**yaml.load(ymlfile))
INFO:cui:&#1048;&#1089;&#1087;&#1086;&#1083;&#1100;&#1079;&#1086;&#1074;&#1072;&#1085;&#1080;&#1077; &#1082;&#1083;&#1102;&#1095;&#1072; fbhalla@company.net
WARNING:debian.changelog:Found eof where expected first heading
INFO:cui.package:&#1054;&#1073;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1080;&#1077; &#1088;&#1077;&#1087;&#1086;&#1079;&#1080;&#1090;&#1086;&#1088;&#1080;&#1103; prod2 (/home/frado/work/co/cui/cache/prod2)
INFO:cui.package:&#1050;&#1086;&#1087;&#1080;&#1088;&#1086;&#1074;&#1072;&#1085;&#1080;&#1077; debian/21.12.0.19 &#1074; /home/frado/work/co/cui/build/prod2/
INFO:cui.source:&#1052;&#1086;&#1076;&#1080;&#1092;&#1080;&#1082;&#1072;&#1094;&#1080;&#1103; debian/changelog (bullseye) / Frado Bhalla <fbhalla@company.net>
ERROR: no results
INFO:cui.source:&#1057;&#1086;&#1079;&#1076;&#1072;&#1085;&#1080;&#1077; &#1072;&#1088;&#1093;&#1080;&#1074;&#1072; ../prod2-csp_21.12.0.19+deb11.tar.xz
INFO:cui.deb.aptly:&#1069;&#1082;&#1089;&#1087;&#1086;&#1088;&#1090; &#1088;&#1077;&#1087;&#1086;&#1079;&#1080;&#1090;&#1086;&#1088;&#1080;&#1103; product-bullseye
gpg: no default secret key: secret key not available
gpg: signing failed: secret key not available
ERROR: unable to publish: unable to detached sign file: exit status 2
ERROR:cui:&#1054;&#1096;&#1080;&#1073;&#1082;&#1072; &#1087;&#1091;&#1073;&#1083;&#1080;&#1082;&#1072;&#1094;&#1080;&#1080; &#1088;&#1077;&#1087;&#1086;&#1079;&#1080;&#1090;&#1086;&#1088;&#1080;&#1103; aptly product-bullseye
frado8@comp:/home/frado/work/co/product_g$ export DEBFULLNAME='Bhalla Frado'
frado8@comp:/home/frado/work/co/product_g$ /home/frado/work/co/cui/cui/lbp-auto -b bundle.yml world bullseye
/home/frado/work/co/cui/cui/cui/program.py:86: YAMLLoadWarning: calling yaml.load() without Loader=... is deprecated, as the default Loader is unsafe. Please read https://msg.pyyaml.org/load for full details.
  options.update(**yaml.load(ymlfile))
INFO:cui:&#1048;&#1089;&#1087;&#1086;&#1083;&#1100;&#1079;&#1086;&#1074;&#1072;&#1085;&#1080;&#1077; &#1082;&#1083;&#1102;&#1095;&#1072; fbhalla@company.net
WARNING:debian.changelog:Found eof where expected first heading
INFO:cui.package:&#1054;&#1073;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1080;&#1077; &#1088;&#1077;&#1087;&#1086;&#1079;&#1080;&#1090;&#1086;&#1088;&#1080;&#1103; prod2 (/home/frado/work/co/cui/cache/prod2)
INFO:cui.package:&#1050;&#1086;&#1087;&#1080;&#1088;&#1086;&#1074;&#1072;&#1085;&#1080;&#1077; debian/21.12.0.19 &#1074; /home/frado/work/co/cui/build/prod2/
INFO:cui.source:&#1052;&#1086;&#1076;&#1080;&#1092;&#1080;&#1082;&#1072;&#1094;&#1080;&#1103; debian/changelog (bullseye) / Bhalla Frado <fbhalla@company.net>
ERROR: no results
INFO:cui.source:&#1057;&#1086;&#1079;&#1076;&#1072;&#1085;&#1080;&#1077; &#1072;&#1088;&#1093;&#1080;&#1074;&#1072; ../prod2-csp_21.12.0.19+deb11.tar.xz
INFO:cui.deb.aptly:&#1069;&#1082;&#1089;&#1087;&#1086;&#1088;&#1090; &#1088;&#1077;&#1087;&#1086;&#1079;&#1080;&#1090;&#1086;&#1088;&#1080;&#1103; product-bullseye
gpg: no default secret key: secret key not available
gpg: signing failed: secret key not available
ERROR: unable to publish: unable to detached sign file: exit status 2
ERROR:cui:&#1054;&#1096;&#1080;&#1073;&#1082;&#1072; &#1087;&#1091;&#1073;&#1083;&#1080;&#1082;&#1072;&#1094;&#1080;&#1080; &#1088;&#1077;&#1087;&#1086;&#1079;&#1080;&#1090;&#1086;&#1088;&#1080;&#1103; aptly product-bullseye
```

---

