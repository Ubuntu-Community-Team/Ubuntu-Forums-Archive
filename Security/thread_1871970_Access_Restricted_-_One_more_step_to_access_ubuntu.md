---
title: "Access Restricted - One more step to access ubuntulinuxhelp.com"
date: 2011-10-29
forum: Security
---

### Post by jsandhu on 2011-10-29
Hi,

I have started using Ubuntu, few weeks back, I was a windows user before and I am quite satisfied and happy with the switch so far, the reason why I am here is I have suddenly started getting a warning when visiting few webpages such as ubuntulinuxhelp.com, the warning I am getting is that my pc is infected with virus and hence I don't have the right to access the webpage, Now, if I was on windows at this point I would run a virus scan, but since I am not and I have read and was told that Ubuntu don't need an antivirus, How should I go about dealing with problem, I am adding a screenshot of the warning page, Kindly take a look: -

---

### Post by jramshu on 2011-10-29
Are you using a proxy or tor or something?

I get those warnings sometimes with the above mentioned.

---

### Post by jsandhu on 2011-10-29
No sir, using my wired connection as it is.

---

### Post by jramshu on 2011-10-29
I hate to tell you, but your ip is showing up on 14 blacklists. That's why CloudFlare is blocking you.

---

### Post by jsandhu on 2011-10-29
ok, where are these blacklists, sorry I don't know much about this stuff.

---

### Post by OpSecShellshock on 2011-10-29
Here are some more details. Sorry. Folks here might be able to assist.

EDIT: link displaying IP removed.

(here I'm presuming displaying your IP address is acceptable since it's in the screenshot. Staff, please remove if that's not the case)

---

### Post by jramshu on 2011-10-29
Sent you a pm.

Maybe you have acquired an ip that a former spammer, or cracker has used and that's why it's showing up on the blacklist.

---

### Post by jramshu on 2011-10-29
> **OpSecShellshock said:**
> Here are some more details. Sorry. Folks here might be able to assist.

[http://www.projecthoneypot.org/ip_edited_out](http://www.projecthoneypot.org/ip_edited_out)

(here I'm presuming displaying your IP address is acceptable since it's in the screenshot. Staff, please remove if that's not the case)

Probably not a good idea security wise. I sent a pm to the op saying the same thing.

---

### Post by lisati on 2011-10-29
> **jsandhu said:**
> ok, where are these blacklists, sorry I don't know much about this stuff.

Have a look at [http://lisati.homelinux.com/rbltest](http://lisati.homelinux.com/rbltest) or [http://lisati.homelinux.com/blacklist](http://lisati.homelinux.com/blacklist)

---

### Post by jsandhu on 2011-10-29
this is too deep for me to understand.. I think I will leave it as it is, it's going over my head.

is there something I can do about it or just forget about it and enter the captcha whenever I ran into a trouble like this?

---

### Post by jsandhu on 2011-10-29
ok if my ip showing is dangerous or something, probably best if admins would delete this thread pls.

---

### Post by jsandhu on 2011-10-29
I deleted the image containing the ip but some of the posts made by others show it, so if it is ok, kindly remove them.

---

### Post by jramshu on 2011-10-29
You'll have to use the captcha, or clear it up with everyone that has the ip flagged. You could try and get a different ip address from isp.

EDIT: removed ip address.

---

### Post by OpSecShellshock on 2011-10-29
It's possible (though not definite) that the malicious activity occurred prior to switching, given that it happened in the last few weeks and the most recent report says "within the last 4 weeks." That would be a best-case, though still certainly not ideal. Given the pharmaceutical nature of the spam, there was almost certainly a compromised computer at that IP address at the time of the activity.

---

### Post by lisati on 2011-10-29
> **jsandhu said:**
> ok if my ip showing is dangerous or something, probably best if admins would delete this thread pls.

No need for that, your IP address isn't dangerous. Please go to [http://voogdnz.net/blacklist](http://voogdnz.net/blacklist) and you will be given instructions on what you need to do.

---

### Post by jsandhu on 2011-10-29
I am on dynamic IP, I turned off my modem, reconnected and this is what I get when I go to ubuntulinuxhelp.com : -

:) problem solved, I guess

---

### Post by jramshu on 2011-10-29
It's good that you posted the question, that way if others run into it they will know why they are running into the same problem.

I generally see that sort of stuff when using tor or a proxy.

EDIT: I was about to say, just reset the modem. lol. Good you got it.

---

### Post by jsandhu on 2011-10-29
haha, thanks but you were the one to actually point out to me that its my IP, thanks to you and all the others for their help.

---

### Post by jramshu on 2011-10-29
No problem. 
I have seen these cloudflare challenges before, usually because of a flagged ip address.

---

