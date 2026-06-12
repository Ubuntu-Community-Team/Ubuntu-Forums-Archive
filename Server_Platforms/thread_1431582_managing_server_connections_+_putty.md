---
title: "managing server connections + putty"
date: 2010-03-16
forum: Server Platforms
---

### Post by guilly on 2010-03-16
Hey Guys,

Haven't posted here in quite some time, but I recently got a position as a Enterprise LAN admin and I find myself using putty ALOT to ssh into various servers. Any tips to manage all your connections with putty ?? or any other tools you guy's find easier. My biggest problem right now is that my connection list in putty is getting quite large fast and is becoming a pain finding which server I want since there is no search feature to browse your saved connections with putty

Thanks

---

### Post by KB1JWQ on 2010-03-16
I've never been a huge fan of Putty.  SecureCRT seemed like a better solution from Van Dyke software, but it's payware.

My personal solution was to switch my desktop to MacOS (and it'll be Ubuntu if Lenovo ever delivers my t510) and use command-line ssh with a bash_completion stanza that tab-completes from my ~/.ssh/known_hosts file.

Your mileage may of course vary.

EDIT: Oh, and congrats on the new job.  I'm on freenode if you get stuck on anything that's time sensitive, same nick.

---

### Post by guilly on 2010-03-17
Thanks for the reply.

I may give secureCRT a try, since it's payware that brings another level of complication. However if it's really that good my manager may be willing to purchase some licenses.

---

### Post by shizakapayou on 2010-03-17
If you're in Windows, I'm fond of mRemote.  Tabbed windows, saved sessions, and also supports RDP and IE, so I can admin everything from one window.  It's free, although the project was bought up by a paid app and is no longer developed in the free form.

---

### Post by KB1JWQ on 2010-03-17
SecureCRT has a trial, but it's worth pointing out that I made the switch away from a Windows desktop almost five years ago, so I defer to the wisdom of others regarding good alternatives for sshing into many boxes!

---

### Post by guilly on 2010-03-17
Thanks again,

Yep unfortunetly I must be on a Windows client. I have discovered putty connection manager. Seems like a boosted version of putty. It is still beta but does seem stable.

---

### Post by koenn on 2010-03-17
I don't quite understand what the problem is - you're always going to have to know at least the server's hostname to connect to it, no matter what program you use, right ? 

Anyway, I sometimes have to deal with multiple linux servers myself (while our workstations are windows), so I've installed a virtual ubuntu desktop on one of our ESXs, which I can use through vmware's VI client, or export its desktop to Xming on my Windows PC. This allows me to manage ssh, rsync, nfs, etc. from a linux environment, which helps to makes things easier sometimes. 

other than that, it's all putty and WinSCP, and some easy to remember names and aliases in DNS.

---

### Post by guilly on 2010-03-18
> **koenn said:**
> I don't quite understand what the problem is - you're always going to have to know at least the server's hostname to connect to it, no matter what program you use, right ? 


The problem is finding the hostname or ip in my connections list (Trying to avoid having to type in the hostname/ip every time). When you have 400+ servers that you are managing things can get pretty hairy. 

As for the ESX idea, that's a good idea and I will keep that in mind if ever I see a need for it. 

If anyone is interested, I've been using this app for the pass few days and it seems quite usefull. It's a C# application and is designed strictly for windows.

puttycm.free.fr/

---

### Post by jrssystemsnet on 2010-03-18
> **guilly said:**
> The problem is finding the hostname or ip in my connections list (Trying to avoid having to type in the hostname/ip every time). When you have 400+ servers that you are managing things can get pretty hairy. 

I'm relatively certain that if you single-click any of the items in the connection list, pressing a key will jump you to the first entry in the list starting with that key.

For example click "a.aaaserver.net", press k, and jump straight to "k.aaaserver.net".  Not sure how it handles multiple keypresses (whether it treats each one as a first-letter jump, or tries to do an autocomplete-style jump); and I don't have a Windows box handy at the moment to test it. :)

---

### Post by guilly on 2010-03-18
> **jrssystemsnet said:**
> I'm relatively certain that if you single-click any of the items in the connection list, pressing a key will jump you to the first entry in the list starting with that key.

For example click "a.aaaserver.net", press k, and jump straight to "k.aaaserver.net".  Not sure how it handles multiple keypresses (whether it treats each one as a first-letter jump, or tries to do an autocomplete-style jump); and I don't have a Windows box handy at the moment to test it. :)

Putty only allows Single keystroke search, so it isn't much use.

---

### Post by jonabyte on 2010-03-19
I keep the hostnames on a text file on my desktop and copy/paste, helps that there is only one username to use and less than five passwords.

---

