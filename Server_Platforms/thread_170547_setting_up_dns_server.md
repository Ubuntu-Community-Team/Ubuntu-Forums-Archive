---
title: "setting up dns server"
date: 2006-05-04
forum: Server Platforms
---

### Post by rocarm on 2006-05-04
Hey guys, 
i have a static IP address, and i've registered a domain name, how can i set up DNS, and get a name server or two (or ip addresses) to point the domain to?

and one more question do i need two ip address to have 2 name servers?

thanks

---

### Post by linuxusr50 on 2006-05-04
Unless you are looking for experience in setting up a DNS server you should consider having you ISP add a record to their DNS that points to your IP.  Several ISP's will do this at no additional cost.  Many times an email to hosmaster@yourisp with your request will do the trick.

---

### Post by rocarm on 2006-05-04
i'm looking for experience, and i know my isp won't do it.. i don't want to run an open server, it'll be just so i don't have to remember the ip address when i want to work from home. can you give me somewhere to start?

---

### Post by linuxusr50 on 2006-05-04
I am not sure I fully understood your last message but if I am reading it correctly you may just need to edit your hosts file and add and entry for your domain.  For this you would do the following.  (I think you will need to run gedit as sudo or root to correctly edit the hosts file).

```
gedit /etc/hosts
```

Then add a line for your IP and domain such as:

X.X.X.X        yourdomain.com

Now you should be able to use your domain name as a substitute for your IP.  The same as you can use the word localhost to subtitute for IP 127.0.0.1.

---

### Post by rocarm on 2006-05-05
thanks, but that only effects this pc. 
i work from home and the server is in the office. 

instead of remembering ip addresses, eg, 55.168.48.24 to get in, i want to type mydomain.com and it resolves to the above ip. from what i understand i have to set up a dns server to do this. 

i'm lost on how to do this.

---

### Post by linuxusr50 on 2006-05-05
A couple of suggestions.

1.  If you have a domain that you have purchased, the registrar has an entry in their DNS that should have a trail all the way to the big 13 root servers that know every domain on the internet.  So the host file should do the trick.

I have included the RFC that is particularly important for setting up DNS servers to help you understand it better.

[ftp://ftp.rfc-editor.org/in-notes/rfc1034.txt](ftp://ftp.rfc-editor.org/in-notes/rfc1034.txt)

If you do put in a DNS server you will likely have problems with secure sites (https).  This would be caused by conflicting entries between your DNS server and your ISP's server.  Many of these sites require proper forward and reverse addressing to function properly.

For example:

Lets say you wanted to go to [https://somewhere.com](https://somewhere.com).

Your machine will query your DNS server who will have no idea about this domain. It will send a response to your ISP's domain server which may or may not know who this is, and so on until some dns server knows this domain and is able to direct your request properly.  Now the secure site responds by making a request that tracks your IP back to its source which ultimatly will be your DNS server which should respond  with information indicating your domain and IP are a matched set.

The problem comes in with the fact that your ISP will have and entry in there DNS that says your IP X.X.X.X  = dsluser 0-15-who knows what else. (i.e. some scheme they have decided to use to keep track of their users).  This means the secure site (i.e. banking or webmail or whatever) will have a mismatch {{your dns server saying one thing and your ISP's saying another}}.  Many secure sites do not like this and will respond by not loading, crashing after loading, or slow downloads etc.

Also you indicated you did not want any external servers.  By there nature DNS servers have to be publicy accessable or they would not work.  To be compliant with RFC Standards you should have two DNS servers, one as a back up to the other though many times this is not done.


I hope this helps.  I am not trying to scare you off of learning about DNS by setting up a working system.  I am just trying to let you know some of the problems you may encounter.

---

### Post by rocarm on 2006-05-05
thanks, i'll have a read through, the ubuntuguide has a little something i've been told as well so i'm going to check that out. 

and i think i confused you, i'm aware how DNS works, and the implications of creating a dns server, i've been in the IT game for well over 10 years, i'm just uncertain on the steps i need to take to create one locally (i'm a developer, not a network admin).  It will be broadcast over the internet, and by publically, i meant open to every tom dick and harry. it'll be password protected, etc. etc. 

thanks for all your help, that document is worth a read, i'm going to print it out and read it on the john tonight ;)

---

### Post by linuxusr50 on 2006-05-05
I still think an entry in the /etc/hosts file is exactly what you are looking for.  Your hosts file could contain an entry like the following and it should work fine.  We use this technique to access our routers that are all over the place.

```
sudo gedit /etc/hosts
```


Edit your hosts file with the following entry. (using the IP you gave in your example).

55.168.48.24          domainofyourserver.com


Then save the file.


You should then be able to use the name of your server interchangeably as a replacement for the IP number.

For example:

```
ssh username@domainofyourserver.com
```

---

### Post by rocarm on 2006-05-05
but it only works on that machine, it doesn't reslove across the internet.. it doesn't tell those 13 dns mega computers that information, and thats what i'm after. 

at home i use XP, and damned if i know how to do it on XP.

---

### Post by linuxusr50 on 2006-05-05
You do it the same on XP.  Your hosts file on XP sets in the following directory.

C:\windows\system32\drivers\etc\hosts

It can be edited with a text file editor like notepad.

The beauty of this is that it doesn't have to resolve accross the internet.  Your computer has already done the work and you are going directly to the IP.  The hosts file did the translation.

---

### Post by rocarm on 2006-05-05
thanks mate, you've been a great help!

---

### Post by chuck jessup on 2008-04-05
ok then to add to his question I have a domain and lamp installed, bind9 and the works (im new at this so please set me straight) 

i have been told to host the site the dns is a must and so (since i am cheap) i dont want to pay 30 some odd $$ for a website dns service, that and its for a game site, no sales or income but i would like it to be seen when ever you type in 'http://www.mynewsite.com' i cant afford to have some one else host it, and im trying to learn (longtime windows user) 

is there a way to set it up that i am not seeing, is it something that is way over my head? help me i am sooo lost :'(


thanks in advance,

J Fender

---

### Post by p_quarles on 2008-04-05
Moved to Server Platforms. 

> **chuck jessup said:**
> ok then to add to his question I have a domain and lamp installed, bind9 and the works (im new at this so please set me straight) 

i have been told to host the site the dns is a must and so (since i am cheap) i dont want to pay 30 some odd $$ for a website dns service, that and its for a game site, no sales or income but i would like it to be seen when ever you type in 'http://www.mynewsite.com' i cant afford to have some one else host it, and im trying to learn (longtime windows user) 

is there a way to set it up that i am not seeing, is it something that is way over my head? help me i am sooo lost :'(


thanks in advance,

J Fender
May I suggest, in the future, that you start a new thread rather than bumping one that's two years old?

---

