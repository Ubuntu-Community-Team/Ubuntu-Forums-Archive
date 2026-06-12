---
title: "webserver access for 50 users in windows environment ?"
date: 2007-08-10
forum: Server Platforms
---

### Post by ricoos on 2007-08-10
I have used ubuntu on my desktop for several months and now that i have some trust in the product I would like to use it where i work in a school for pupils to use , initially accessing the webserver.

The network is a manged windows network with active direxctory as directory service, can say 50 users have a dsirectory each on the webserver ?  If so , how can they access their own server space and how could it be authenticated for security.

Is it easy to get ubuntu desktop to tie in with AD, as there seems to be several ways to do it , but which one works , can you also redirect home folders from  a windows 2003 server? And are desktops affected by any windows group policies 

sorry for the hundreds of questions , but i would prefer to use ubuntu than windows any day, as long as it works and can work seamlessly and without loosing ones hair.

cheers

hopefully future linux user

---

### Post by HermanAB on 2007-08-10
Getting ADS to work with Linux requires a little bit of patience.  See this: [http://aeronetworks.ca/LinuxActiveDirectory.html](http://aeronetworks.ca/LinuxActiveDirectory.html)

Cheers,

Herman

---

### Post by koenn on 2007-08-11
herman: your howto looks interesting, I'm going to have to try that one of these days. 

rocoos:
> can say 50 users have a dsirectory each on the webserver ?
yes

>  If so , how can they access their own server space and how could it be authenticated for security.
anyway you decide. ftp is the classic method. samba might work. 

> Is it easy to get ubuntu desktop to tie in with AD, as there seems to be several ways to do it , but which one works , 
re Hermann

> can you also redirect home folders from a windows 2003 server? 
you can mount smb shares in a Linux filesystem. 


> And are desktops affected by any windows group policies
Linux desktops ? No. 

```
sorry for the hundreds of questions , but i would prefer to use ubuntu than windows any day, as long as it works and can work seamlessly and without loosing ones hair
```

There are no garantuees about loss of hair, time, data, social life, and  girlfriends.

---

