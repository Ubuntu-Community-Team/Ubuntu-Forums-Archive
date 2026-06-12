---
title: "ARGH!!!Newb issues with LAMP"
date: 2008-04-08
forum: Server Platforms
---

### Post by chuck jessup on 2008-04-08
ok i have an apache server i am setting up to host a single site for a game i play (EVE online) and have had nothing but trouble, i have never done servers before and this was recommended to me, as "easy" i must not be catching on so quickly... i have had to reload LAMP several times to get it to host the sites domain(e.g. 'www.mydomain.com') on my home 'server' and get it host the site, (dont get me wrong i love ubuntu, it is awesome how easy it is to learn... but i am a windows baby) ummm well my issue is how do i get apache started? there is a ton of stuff on the forums, i get a line erroir, about apache can not determine the servers fully qualified domain name, using 127.0.1.1 for server name. 

i am sooo frustrated and cant figure out what to do... please help me in a simple way that i might be able to get this all set up. I WANA CRY!!!!!lol... 

thanks in advance

---

### Post by scragar on 2008-04-08
If it say's that it cannot determin domain name then it defaults to
[localhost](http://localhost), but other visitors will need to enter your IP. If you have a domain from somewhere you should ask them, they will proberly have better guides than I could offer.

---

### Post by chuck jessup on 2008-04-08
i have they want to charge me to upgrade my profile to get 'free' support (the reason i am doing this is well i want to learn, and that i cant afford hosting, so i wanted to do it myself, it however has become evident that if i wish to get it set up i may just have to suck it up and pay them to do it for me... 

is there a config file that allows me to edit the name servers ( i have that info--) and or put the domain name in ... this is the only thing keeping me from hosting, if there is a file i can edit to get the server to recognize it and then it should be able to start... ( i just reloaded it again) so i have a fresh start to play with... i want to learn, but--- i should have been content with just having the desktop, i am way over my head (even if the software comes pre-config'ed) however i have invested the money now... and am deturmined... 

again there should be a file or something to edit to tell it that it is supposed to be doing... 

thanks again in advance

---

### Post by scragar on 2008-04-08
it involves a few edits:
```
gksudo gedit /etc/hosts
```
add a space after the word localhost and put in the domain name.

you will also need to edit the file in sites-enabled:
```
gksudo /etc/apache2/sites-enabled/`ls /etc/apache2/sites-enabled/`
```
make sure "Deny from all" is not enabled.

then you'll need to set up your domain with their services.

---

### Post by chuck jessup on 2008-04-08
i boo boo'ed so im re installing-- then ill give it a shot - thanks... let ya know if that helps too.

thanks again :)

---

### Post by chuck jessup on 2008-04-09
HAHA! It worked!!! Thank You sooooooooooooooo much :-D...

I had to edit the files in xubuntu, i apt-get install gkedit and it dl'd, unpacked, and installed, but wouldnt open -- 

but no matter- Thank you So very much.

---

