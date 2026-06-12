---
title: "Has my wireless been compromised?"
date: 2011-12-14
forum: Security
---

### Post by veroslav on 2011-12-14
Hi,

I am running a dual-boot (Ubuntu 11.10/10.10) and last saturday, I switched from 10.10 to 11.10 and
noticed that I couldn't connect to my wireless. Whatever I did it wouldn't connect.

So I logged back in to 10.10 and same problem there! So I disconnected my router and plugged it in
the computer in order to reconfigure it (change password). I couldn't change password for some
reason, but I could connect to the router directly from the computer so I decided to try to connect
wirelessly again. It worked! So everything was good. It has happened many times before that my
router drops the connection so I wasnt worried at all.

Starting on monday, I noticed there were no incoming connections when downloading torrents, never.
I could download, but nobody could connect to me. This happened previously once or twice, and after
what happened on saturday, I suspected another router related issue.

So yesterday, I logged in on the router wirelessly (used no password for the admin there) and when fiddling with
the wireless configuration, suddenly I saw what appeared to be another client connected to it!
Under the DHCP dynamic clients section (or something like that) connected to router, I saw my own
computer, and another machine I couldn't recognize. 

The hardware address of that machine was different from mine, and the IP was same as mine but
one greater (mine was xxx.xxx.xxx.xx0 and the other was like xxx.xxx.xxx.xx1). This machine had no
name.

I freaked out and disconnected the router immediately, unfortunately, in the panic, I didnt write down
the details of the other connected client. Now, I am using a PS3 sometimes, and it also is using the same connection to the router when active, but I wasn't using it at the time.

I was using WPA/WPA2 Personal and a password consisting of numbers, different case letters and a '!'.
It was of length 12. I also used the same password for one of my Ubuntu's login.

I took a quick glance at auth.log and sys.log (I think it was) and didnt find anything strange happening
yesterday.

I also changed the password to both the router (using a mixture of symbols, letters, and numbers)
with length 60 and the Ubuntu that had the same password as the router before. I am still using
WPA/WPA2 Personal.

However, I cant relax at the moment as I am afraid my computer and login has been compromised.
I havent noticed any other weird behaviour with my computer other than the above.

Please, could you advise me on how to proceed and what to do next?. I am thinking of re-installing
the Ubuntu as well, is it over the top? I am VERY worried!

Thank you in advance for your fast reply!

Kind Regards,
Veroslav

---

### Post by Ms. Daisy on 2011-12-14
If it were me, I would reset the router & create a new good password (the one you described sounded pretty decent) & user name. I wouldn't reuse any passwords.  Simply for the peace of mind it would afford you, I would also just reinstall ubuntu.

You may want to look into keyrings if you want to use really long complicated passwords for everything.

Are you sure the other machine you saw wasn't a printer or some other device you've got on your network?

---

### Post by veroslav on 2011-12-14
Thank you for your reply!

I was going to change all of my passwords, just for a piece of mind as you said. Will keep monitoring the router for any suspicious devices connecting after I change the passwords and see how it goes.

I am not aware of any other devices (other than my PS3, which was off at the time, and my cell phone, that has wireless connectivity disabled) that I sometimes connect to my wireless.

I am more and more inclined to think that it was something I missinterpreted when checking the router settings, but I will change both my login and wireless passwords to a more secure ones.

If anybode else has any more input on this, I would love to hear from you. I've read the security wiki on here, but any good practice advices that apply to my situation will be highly appreciated.

Thanks again.

Kind Regards,
Veroslav

---

### Post by haqking on 2011-12-14
turn on mac filtering to only allow approved clients and turn off ssid broadcast and change the ssid also.

This can all be circumvented but gives you a little more security.

Always try to use WPA2 where possible and 63 chr keys that are combinations of various upper and lower case and special characters. and non dictionary words or phrases

something like

```
JG8jg6YIyht&lGi5,jcFJ\qo%L83Ihwcy%AT/jmyFUt!kR\h1WxJQd+Ky4M7k9j
```

504 bit/63 chr key

cheers

---

### Post by veroslav on 2011-12-14
Thank you Haqking,

that is precisly in line with what I was going to do later today when I am at home! :)

Glad to hear that my thinking was right, thanks very much.

Kind Regards,
Veroslav

---

### Post by jeremywc on 2011-12-14
I don't know that you need to reinstall your OS just because your wireless network was compromised. I'd review all the copies of /var/log/auth.log for any strange authorizations. If everything looks good, it's unlikely that they were able to break into your machine. Especially if you aren't running sshd or any other RATs.

---

### Post by OpSecShellshock on 2011-12-14
It may also be worth checking the manual of your game console to see if it maintains the wireless connection when powered off. I know some of them do.

---

### Post by Dangertux on 2011-12-14
pro tip : Generate 63 character passphrases quickly on the fly by doing the following  

```
 cat /dev/urandom | tr -dc _A-Z-a-z-0-9 | head -c63 
```

---

### Post by josephmills on 2011-12-14
I would also do what everyone else is saying about resetting your router and adding a new big passwd (over 30 characters )On some routers you can also make it so that only certain MAC address are allowed on to the network. This can be helpful for you wireless network. Hope this helps and good luck.

---

### Post by fdrake on 2011-12-14
another suggestion to add to the previuos ones:
1- change the default pass of the admin user of the router
2- disable remote management/mantainance 

if your issue persists check the routers logs-connection status

---

### Post by Ms. Daisy on 2011-12-14
> **Dangertux said:**
> pro tip : Generate 63 character passphrases quickly on the fly by doing the following  

```
 cat /dev/urandom | tr -dc _A-Z-a-z-0-9 | head -c63 
```
ooh- good tip!

---

### Post by Dangertux on 2011-12-15
> **Ms. Daisy said:**
> ooh- good tip!

And if you want special characters

```

/dev/urandom | tr -dc A-Z-a-z-0-9-"'_*(#&@$*)&'" | head -c63

```

---

### Post by veroslav on 2011-12-15
Hi again!

Thank you so much for such an amount of great tips. I've changed the password to a longer one and implemented other suggestions as well, so now I feel much calmer.

OpSecShellshock's suggestion might be correct though! I connected my PS3 yesterday and monitored the connected devices on my router. One hour after I disconnected the PS3, it was still displaying as connected!

I will keep an eye on this tonight when I am at home and check whether it still shows as connected. If yes, then it was probably it and not a neighbour that kept me from sleeping two nights before :)

Thank you all again!

Kind Regards,
Veroslav

---

### Post by OpSecShellshock on 2011-12-15
> **Dangertux said:**
> And if you want special characters

```

/dev/urandom | tr -dc A-Z-a-z-0-9-"'_*(#&@$*)&'" | head -c63

```

APG works for that as well, but the command isn't nearly as cool:

```
apg -a 1 -n 1 -m 63 -M SNCL
```

You can substitute -a 0 or leave the -a option out entirely to get something considered "pronounceable" (it still isn't a word, but it has a sort of phonetic cadence to it, I guess).

---

### Post by Ms. Daisy on 2011-12-15
> **veroslav said:**
> OpSecShellshock's suggestion might be correct though! He usually is.

Now I'm going to have to open some new accounts somewhere so I can use all these cool passwords I'm generating! LOL

---

### Post by dodo3773 on 2011-12-15
Instead of just looking at the connected ip addresses take note of the mac addresses associated with each device you own. Then when you log into your router or do an nmap scan you can compare them to your existing devices.

---

### Post by haqking on 2011-12-15
> **dodo3773 said:**
> Instead of just looking at the connected ip addresses take note of the mac addresses associated with each device you own. Then when you log into your router or do an nmap scan you can compare them to your existing devices.

he did do that

from OP

> So yesterday, I logged in on the router wirelessly (used no password for the admin there) and when fiddling with
the wireless configuration, suddenly I saw what appeared to be another client connected to it!
Under the DHCP dynamic clients section (or something like that) connected to router, I saw my own
computer, and another machine I couldn't recognize. 

[B]The hardware address of that machine was different from mine, and the IP was same as mine but
one greater (mine was xxx.xxx.xxx.xx0 and the other was like xxx.xxx.xxx.xx1)[/B]. This machine had no
name.

And as mentioned these are easily spoofed anyways.

Regardless it looks like it was the PS3 hangin around after a poweroff which they do sometimes in routers cache.

Cheers

---

