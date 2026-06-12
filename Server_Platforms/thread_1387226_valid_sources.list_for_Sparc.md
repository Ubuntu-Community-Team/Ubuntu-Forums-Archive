---
title: "valid sources.list for Sparc"
date: 2010-01-21
forum: Server Platforms
---

### Post by b4nsh33 on 2010-01-21
Hello to all i have a recicled sun fire v240 that i need to use for central loging server, i got an ubuntu 7.10 cd that  i got to install succefully in the server.
So foar so good, the problem now is that i cant install any software, everytime i run apt-get update the error says:

Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Sources
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Packages
  404 Not Found [IP: 91.189.88.30 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Packages
  404 Not Found [IP: 91.189.88.30 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Sources
  404 Not Found [IP: 91.189.88.30 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Sources
  404 Not Found [IP: 91.189.88.30 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Packages
  404 Not Found [IP: 91.189.88.30 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Sources
  404 Not Found [IP: 91.189.88.30 80]


I guess the old repositories configured in the old 7.10 iso are no longer valid, where can i find a valid one?
kind regards

---

### Post by cdenley on 2010-01-21
[http://www.ubuntu.com/news/ubuntu-7.10-eol](http://www.ubuntu.com/news/ubuntu-7.10-eol)

There is no gutsy repo anymore.

---

