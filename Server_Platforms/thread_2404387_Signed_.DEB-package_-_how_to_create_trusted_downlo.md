---
title: "Signed .DEB-package - how to create trusted download archive?"
date: 2018-10-23
forum: Server Platforms
---

### Post by Elmi77 on 2018-10-23
[COLOR=#242729][FONT=Arial]Hi,

for some time I sign my .DEB-packages with
[/FONT][/COLOR]
[FONT=courier new]sudo dpkg-sig --sign builder mypackage.deb[/FONT]
[COLOR=#242729][FONT=Arial]
This seems to be successful, after signing the .DEB package is larger. Now I have a server where these packages are available at e.g. a location[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial][URL="https://www.mypage.tld/download/Linux/Ubuntu/dists/bionic/main/binary-amd64/"]
https://www.mypage.tld/download/Linux/Ubuntu/dists/bionic/main/binary-amd64/[/URL][/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
...of course with a Packages.gz so that it can be installed with "apt-get install" when the path is added to the sources.list[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]My question: what do I have to do in order to see these packages as "trusted" during install, means in order to let apt-get verify the packages against the signature?[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Thanks![/FONT][/COLOR]

---

