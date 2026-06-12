---
title: "how does my colleague's Proxy Server work?"
date: 2012-03-09
forum: Server Platforms
---

### Post by RandomCharacters on 2012-03-09
At school most decent websites are blocked. Recently a friend of mine emailed me the information required to connect to some guy in my class's proxy. thing is i'm not supposed to be using it.

so my question is how does his server work?

i'm new to the whole linux thing but i have successfully installed Ubuntu on a partition of my hard drive.

well the information given to me was a login id
a password

a version of putty called "secure", ironically when i run it, it promps me that it was tampered with and may not be secure

and a set of instruction, that instruct me to add:
socks v5 127.0.0.1 port 8080
to the "manual proxy" setting in firefox

finally when i run the "secure" file (putty) i do as follows:
[IMG]http://i.imgur.com/vgrRC.png[/img]
(i censored the user id)
and voila i can surf any website

My final question is how could i make a similar server at home to avoid using colleague's.

Thanks for reading

---

### Post by d4m1r on 2012-03-09
So you're an employee of the Ottawa-Carleton District School Board? ;)

As for the proxy, my guess is they are running a program called "Squid" which acts as an HTTP proxy and you can read the instructions to set it up @ [https://help.ubuntu.com/](https://help.ubuntu.com/)

Just pick the version of Ubuntu you are using, Server Guides, and look for squid.

---

### Post by RandomCharacters on 2012-03-09
> **d4m1r said:**
> So you're an employee of the Ottawa-Carleton District School Board? ;)

As for the proxy, my guess is they are running a program called "Squid" which acts as an HTTP proxy and you can read the instructions to set it up @ [https://help.ubuntu.com/](https://help.ubuntu.com/)

Just pick the version of Ubuntu you are using, Server Guides, and look for squid.

thanks for the response,

actually i'm a student

i've been doing research on setting up a squid server
what i can't seem to find in the help.ubuntu manual is an explanation on how i'd connect to the server with a windows pc

---

### Post by d4m1r on 2012-03-09
> **RandomCharacters said:**
> thanks for the response,

actually i'm a student

i've been doing research on setting up a squid server
what i can't seem to find in the help.ubuntu manual is an explanation on how i'd connect to the server with a windows pc

I was a student there myself only 3-4 years ago (not Merivale H.S but close enough ;) )...As for connecting to a Squid server, it should be running a mini webserver for it so you'd access it by going to [http://your.ip.here:8080](http://your.ip.here:8080) or [https://your.ip.here:8080](https://your.ip.here:8080)

OR, if its a SOCKS proxy, you would browse through your internet browser of choices settings looking for anything related to proxy and enter the IP + port 8080 there.

---

### Post by lovinglinux on 2012-03-13
Please do not try to circumvent your school network policy.

We do not condone such activity here.

For more information, please see the forum policy: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

Closing.

---

