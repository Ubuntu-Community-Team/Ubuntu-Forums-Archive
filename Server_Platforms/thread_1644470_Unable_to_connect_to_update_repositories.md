---
title: "Unable to connect to update repositories"
date: 2010-12-13
forum: Server Platforms
---

### Post by mwbutler on 2010-12-13
Hi
 
I have just installed 10.10 on a server fine and am trying to run
 
```
sudo apt-get update
```
 
but everytime it returns saying
 
```
failed to fetch <url> unable to connect to <url>
```
 
I can ping the server from the windows network fine, added it to DNS and made sure the repository websites are unfiltered (I work in a school).
 
I added the proxy into /etc/bash.bashrc so it looks like this:
 
```

<cut to bottom of the file>
export http_proxy=http://<myuser>:<mypass>@proxy.<location>.org.uk:<port>
export ftp_proxy=http://<myuser>:<mypass>@proxy.<location>.org.uk:<port>

```
 
and still no joy.
 
Does anyone have any tips so I can get this working?
 
Cheers
 
PS I have yet to install a D.E but that's my next task.
 
edit
 
I have a laptop running 10.10 desktop version and that can run the update command fine.

---

### Post by fistv on 2010-12-13
There is something going on for the past 3 days or so, I've not been able to get quite a few updates downloaded and when they do I get a size mismatch.

---

### Post by sikander3786 on 2010-12-13
Go to Software Center > Edit > Software Sources > Change Update Server to something else than the current one, preferably Main Server.

Try apt-get update again. If it still returns some errors, we need to see the complete output of that command.

---

### Post by mwbutler on 2010-12-13
> **sikander3786 said:**
> Go to Software Center > Edit > Software Sources > Change Update Server to something else than the current one, preferably Main Server.

Try apt-get update again. If it still returns some errors, we need to see the complete output of that command.

I don't have a gui installed yet so I can't and if I try to install one it says it cannot find the package.

---

### Post by karthick87 on 2010-12-13
Post the complete output of,

```
sudo apt-get update
```

---

### Post by mwbutler on 2010-12-13
> **karthick87 said:**
> Post the complete output of,

```
sudo apt-get update
```

When I'm at work tomorrow I'll do that but it's just what I've put in my original post. 

Is there any way to get a command to save the output to a text file? Then how would I copy it to a memory stick? As I don't feel like typing out the entire output.

Thanks

---

### Post by karthick87 on 2010-12-13
Yes execute the following command,

```
sudo apt-get update > 1.text
```

Then move the file 1.text to your thumb drive..

---

### Post by mwbutler on 2010-12-14
> **karthick87 said:**
> Yes execute the following command,
 
```
sudo apt-get update > 1.text
```
 
Then move the file 1.text to your thumb drive..
 
Thanks for that. Here's the output:
 
```

Err http: maverick Release.gpg
  Unable to connect to :http:
Err http:/archive.ubuntu.com/ubuntu/ maverick/main Translation-en
  Unable to connect to :http:
Err http:/archive.ubuntu.com/ubuntu/ maverick/main Translation-en_GB
  Unable to connect to :http:
Err http:/archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
  Unable to connect to :http:
Err http:/archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_GB
  Unable to connect to :http:
Ign http: maverick Release
Ign http: maverick/main Sources
Ign http: maverick/restricted Sources
Ign http: maverick/main amd64 Packages
Ign http: maverick/restricted amd64 Packages
Err http: maverick/main Sources
  Unable to connect to :http:
Err http: maverick/restricted Sources
  Unable to connect to :http:
Err http: maverick/main amd64 Packages
  Unable to connect to :http:
Err http: maverick/restricted amd64 Packages
  Unable to connect to :http:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates Release.gpg
  Could not connect to gb.archive.ubuntu.com:80 (194.169.254.10). - connect (110: Connection timed out)
Err [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
  Unable to connect to gb.archive.ubuntu.com:http:
Err [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_GB
  Unable to connect to gb.archive.ubuntu.com:http:
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates Release
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/universe Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/universe amd64 Packages
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/universe Sources
  Unable to connect to gb.archive.ubuntu.com:http:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/universe amd64 Packages
  Unable to connect to gb.archive.ubuntu.com:http:
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (110: Connection timed out) [IP: 91.189.88.37 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_GB
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_GB
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_GB
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_GB
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main amd64 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted amd64 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe amd64 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse amd64 Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main amd64 Packages
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted amd64 Packages
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe amd64 Packages
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse amd64 Packages
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates Release.gpg
  Could not connect to archive.ubuntu.com:80 (91.189.88.45). - connect (110: Connection timed out) [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_GB
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_GB
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_GB
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release.gpg
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_GB
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_GB
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/main amd64 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/restricted amd64 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/multiverse amd64 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe amd64 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/multiverse amd64 Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/main Sources
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/restricted Sources
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/multiverse Sources
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/main amd64 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/restricted amd64 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/multiverse amd64 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe Sources
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/multiverse Sources
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe amd64 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/multiverse amd64 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.45 80]

```
 
Cheers

---

### Post by mwbutler on 2010-12-14
I have just reinstalled the server and when I run
 
```
sudo apt-get update
```
 
it now says 
 
```
temporary failure resolving <proxy>
```
 
Any ideas? Can't find any answers on google atm...still looking.
 
Cheers

---

### Post by mwbutler on 2010-12-14
Problem solved!
 
In /etc/apt/apt.conf I tinkered with the proxy and apt-get update finally works!

---

