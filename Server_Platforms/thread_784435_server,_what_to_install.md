---
title: "server, what to install"
date: 2008-05-06
forum: Server Platforms
---

### Post by Mr_Whippy on 2008-05-06
Hi all,

I am currently trying to install a ubuntu server, when its up i wont to run a test domain on it, however im not sure about the setup i have an idea as to how i will set it up but thought i would ask here first.

firstly, i am hoping eventually to get a windows server running alongside the ubuntu server(2008, purely to see how its done and to see if i can intergrate them).

i will be using both an ubuntu client and a windows client on the domain as well.

I would like the server to have a LAMP setup, plus filesharing with openldap (to emulate an AD type control on the domain, i have found a tutorial for this).

I will also be wanting remote access for two reasons, one to work on projects stored on the server, im thinking vpn onto the domain, not sure if i need to then control one of the clients to be able to work here or if i can logon remotely without using citrix, secondly to be able to administer the domain remotley also.

The last thing i can think of right now that i need to be able to do is have logon scripts that run, like you can in a windows server domain for group policy type things etc... 

i was thinking of splittin all this up, so running the ldap and samba on the main server, then virtualising the other bits onto seperate servers so one for LAMP, remote access etc.. 

anyone have anything to say on this, 

please dont just say yes or no, or give me the answer directly, as kind of you as that would be, i would like to have a go at figuring it out, any tutorials you know would be appreciated, however.

thanks in advance steve.

---

### Post by at0mic on 2008-05-15
best plan is to takle all of them one at a time and find a how to or tutorial on installing all the services mentioned either through searching google or here in the forums. shockingly it only takes mere minutes to install any given service once you have a printed tutorial.

---

### Post by Mr_Whippy on 2008-05-16
Yeah i have found a few tutrials now, one on the ubuntu sites somewhere that i have found a link to which looks quite good, ill get back to you all when i have done.

---

### Post by uzi09 on 2009-01-17
> **Mr_Whippy said:**
> Yeah i have found a few tutrials now, one on the ubuntu sites somewhere that i have found a link to which looks quite good, ill get back to you all when i have done.

Any updates on this? I'd be interested in doing something similar. If you've found some helpful guides that have worked for you, please do share :)

---

### Post by Iowan on 2009-01-17
[howtoforge.com]("http://www.howtoforge.com/howtos/linux/ubuntu") has several "perfect server" articles and [help.ubuntu.com]("https://help.ubuntu.com/") is another good place to check.

---

