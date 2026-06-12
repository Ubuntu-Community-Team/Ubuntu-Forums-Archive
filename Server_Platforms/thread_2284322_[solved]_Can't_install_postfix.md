---
title: "[solved] Can't install postfix"
date: 2015-06-28
forum: Server Platforms
---

### Post by adam153 on 2015-06-28
Title says it all. It will not let me install postfix, I've tried searching everything and still no good.  Essentially I now have a website hosted on my VPS (And now a forum.)  I came across the problem of the php mail not working, and after some research found that it requires a mailing service.  I'm not sure if one came prepackaged (I doubt it) but I tried to install postfix and *sigh* got errors.

SCREENSHOT:  [http://i.imgur.com/6MhN9Wy.jpg](http://i.imgur.com/6MhN9Wy.jpg)

---

### Post by darkod on 2015-06-28
The apt-get update shows many errors. Do you have stable internet connectivity of the vps? It's rare not to be able to update apt.

One reason why it shows there is no postfix candidate is if it was never able to update the apt database with the necessary info. In that case it will say there is no postfix to install.

Some providers limit the VPSs to their own repositories. In that case the apt-get update will pull down data from there. But in your case it doesn't seem to be the case. The apt update is looking for security.ubuntu.com.

Also, are you running the 15.04 server? It says vivid in the apt results. In case you do, I suggest you look into reinstalling with 14.04 LTS right away. Don't use standard release for a server. The are supported only for 9 months. In this case for 15.04, support stops next January. LTS releases have 5 years support.

---

### Post by adam153 on 2015-06-28
I do have a stable internet connection both on/off the server.  As for the version, it is indeed currently running 15.04 vivid.  How would I go about downgrading?  Big shrug in terms of all progress I've made so far if I have to essentially reformat.  In terms of the packages available, I think I may be limited.  While the FAQ for ovh isn't very specific, it does say it has its' own mailing service, but it seems as if that's for their website hosting and not their VPS's.  I don't know, I already made a ticket.  I will find that part out soon.

> lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 15.04
Release:        15.04
Codename:       vivid


---

### Post by darkod on 2015-06-29
Unfortunately as far as I know, there is no downgrading. The only way is reformatting and doing everything again. Note that for most applications you can save your current config files and after reinstalling simply use them again. That helps a bit to reach the same configuration a bit faster.

---

### Post by adam153 on 2015-06-30
Support ticket:

> [COLOR=#333333][FONT=inherit]Good day,[/FONT][/COLOR]
Thank you for taking time to contact our support team. As we don't provide
software support, we won't be able to tell you why the installation of Postfix
failed, however if it requires any changes to a kernel parameter, you must
know that the architecture of our VPS Classic is built on a common kernel
shared with every other VPS on the same Host that makes it impossible for us
to make any customization for one customer.


---

### Post by adam153 on 2015-06-30
Ended up getting it all to work with [this](http://askubuntu.com/questions/91543/apt-get-update-fails-to-fetch-files-temporary-failure-resolving-error)

---

