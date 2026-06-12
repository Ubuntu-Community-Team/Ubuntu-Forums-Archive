---
title: "Are these Signs of trying to....."
date: 2012-01-23
forum: Security
---

### Post by VcDeveloper on 2012-01-23
Are these signs of people trying to find vulnerable access through HTTP?

```
[Mon Jan 23 05:51:33 2012] [error] [client 89.252.39.11] invalid request-URI \x92c\xb9\x98\x11\xe2\x01N\x1b\xb1XP\xf0\x81g
[Mon Jan 23 05:51:44 2012] [error] [client 89.252.39.11] request failed: error reading the headers
[Mon Jan 23 10:10:41 2012] [error] [client 87.67.15.115] invalid request-URI R\x15\xea\x9a\xae\x1b\xb9\xc8\x1f<2\xb0n\xbf\xbc\xc1i\xc9!$\xa6aE\xf3\x15\xb0\xde\xff\xba\x18\xb1\xe1\x8c\xcfC\xe2+\x02\x1b\xe7)S'\xdf\x8b\x8d\xd1>\xb2\x01\x17\xa7
[Mon Jan 23 12:09:59 2012] [error] [client 83.25.38.252] invalid request-URI 

```

---

### Post by emiller12345 on 2012-01-24
You might need a little more information here. Are you saying this is a web-server log, and that it's logging client requests? 

I've tried to disassemble the first line directly in 32-bit and 64-bit, but I don't see anything...

```

;i386
global _start
      _start:
      xchg    eax,edx                ;  00000000 92
      arpl    [ecx+0x1e21198],di        ;  00000001 63B99811E201
      dec    esi                ;  00000007 4E
      sbb    esi,[ecx-0x7e0fafa8]        ;  00000008 1BB15850F081
      a16                    ;  0000000E 67

``````

;amd64
global _start
      _start:
      xchg    eax,edx                ;  00000000 92
      db    0x63                ;  00000001 63
      mov    ecx,0x1e21198            ;  00000002 B99811E201
      sbb    r14,[rcx-0x7e0fafa8]        ;  00000007 4E1BB15850F081
      a32                    ;  0000000E 67

```but it could be a lot of other stuff so this doesn't mean much, i.e. if there is random padding it will decompile differently.  It could just be random bytes from a mis-configured client or part of a fuzzing program. Really hard to say.

---

### Post by VcDeveloper on 2012-01-24
Hi, thanks for your help!  Yes, these are web server error logs.  Are these normal and is there a list anywhere that shows a list of patterns to lookout for if someone is trying to test your server for vulnerability?

---

### Post by AgentZ86 on 2012-01-24
> **VcDeveloper said:**
> Hi, thanks for your help!  Yes, these are web server error logs.  Are these normal and is there a list anywhere that shows a list of patterns to lookout for if someone is trying to test your server for vulnerability?

I would say no

client 89.252.39.11 these lines items are the IP but from where this comes from you may not know or if it looks familiar to you

It could be simply someone accessing a page on your webserver that didn't have a correct plugin type, or perhaps no permissions or maybe even typed in the wrong user/password by accident, but this usually results in login attempted failure or some such error message log too.

I get these all the time on my webserver and I would say that without knowing exactly what resource they were accessing or what the user did it may not be enough information to suspect attempted intrusion.
Additionally sometimes with things like a Content site which has group permissions and/or a hierarchy of permissions then someone might be logged in to one set of credentials but then try to access a part of the page that they do not have permission for and thus you get access errrors to especially if they don't even try to login to the extra permissioned portion of the page. So in some cases lets say the accessed your webpage on the server and have access to a part of the page that allows them to input the RSS feed but not add images and they click on something from within there portion of access that they do not have access to such as ADD IMAGE then you would get various types of errors on the logs. but not a login failure attempt assuming they did not try to login but simply closed the page after they realized they could not access that part of the site.

Also it could be an attempt to access a page on your server where some text/feed/image no longer exists and thus spits out an error for that users attempt. Or sometimes if they have an old page in their browse cach and it doesn't update the page and thus could be attempting to access old data as well.

There could be a number of things going on here but the list is probably too broad with this little information

I get this sometimes when my own LAN computer attempts to go to a page on the sever but not though the LAN but through the WAN and because i'm inside the network I can give my self some errors like this on occasion.

Anyhow I hope this helps and I would not be very concerned about an error only

But what would through up a flag for me would be login failed errors many times daily that would make me more suspect to vulnerability but not just http errors in general.

---

### Post by emiller12345 on 2012-01-24
> **VcDeveloper said:**
> Hi, thanks for your help!  Yes, these are web server error logs.  Are these normal and is there a list anywhere that shows a list of patterns to lookout for if someone is trying to test your server for vulnerability?

You could use Snort, there is much information from bodhi here 
[http://ubuntuforums.org/showthread.php?t=1477696](http://ubuntuforums.org/showthread.php?t=1477696)

it may be a little overkill for just a few lines of code, but It might be worthwhile to have an IDS in place for piece of mind.

I believe you can even run previously save *.pcap files at a later date to check if they throw up any red flags.

---

### Post by Dangertux on 2012-01-24
Or a web application firewall like mod-security. 

There is a great post in this thread that explains other possible caused for seeing bytecode entire in your logs. They are not neccessarily indicative of an attempt at exploitation.

---

### Post by VcDeveloper on 2012-01-25
Thank everyone for helping me understand whats going on.  I appreciate it very much!  I will look into Snort and mod-security right away!...

---

