---
title: "LTSP + AD integration"
date: 2012-01-01
forum: Server Platforms
---

### Post by -KaaL- on 2012-01-01
Hello folks,

I have a Windows AD environment with user profiles having homedirs in Windows.
Now I have setup an Ubuntu LTSP Server (10.04.3 - installed via ubuntu-alternate 64bit)

My target was to integrate both these environments, have a single sign-on feature and having their homedirs mapped in Linux as well.

For this purpose I came across this tutorial 
[http://math.univ-lille1.fr/~hafidi/terminal-services/authentication_and_homedirs_on_windows.html]("http://math.univ-lille1.fr/%7Ehafidi/terminal-services/authentication_and_homedirs_on_windows.html")
This exactly suites the kind of environment that I have.

However in this tutorial, I am stuck at Step No. 5.2.2
It says to run authconfig
I don't know what they are referring to here.
I have auth-config-server and auth-config-client installed on ubuntu but still running just authconfig in terminal doesn't work.
Am I missing something here?

Please help me out. 
If there are any other robust free solutions, please also let me know.
Thank you.

---

### Post by rsvancara on 2012-01-01
Authconfig is a tool in Redhat/Fedora based distributions.  It is used configure PAM/NSS to use various authorization/Authentication mechanisms.  You can accomplish the same thing manually if you know what you are doing.  

--
[Know Your Linux]("http://www.knowyourlinux.com/")

---

