---
title: "server download mirror directs to expired domain - possible malicious issue"
date: 2016-09-06
forum: Security
---

### Post by realmx2 on 2016-09-06
I just attempted to download Server 16.04.1 LTS using the download button on the [ubuntu.com]("http://ubuntu.com") website and was greeted with a webpage at [geekcdn.com]("http://geekcdn.com")


It  appears their domain expired or something, you may want to remove from  mirrors, if a bad actor got control of that domain they could serve  up some malicious iso files.

I sent an email to [EMAIL="support@ubuntu.com"]support@ubuntu.com[/EMAIL], but who knows if it will get through, I thought a message on here would double the chances.

Can someone let whoever needs to know this know please, thanks.

-Andy-

---

### Post by cariboo on 2016-09-07
You'd probably be better off creating a bug on bugs.launchpad.net, as the staff here are not in contact with any one at Canoical.

---

### Post by QIII on 2016-09-07
Hello!

I'd say to go ahead and report it as a bug as suggested.

However, I just checked and did not encounter a problem, so you might also consider whether you have encountered a browser hijack rather than an expired mirror.

---

### Post by ian-weisser on 2016-09-07
Mirrors are a Launchpad Group...well, several groups:
[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)
[https://launchpad.net/ubuntu/+cdmirrors](https://launchpad.net/ubuntu/+cdmirrors)

Mirrors are regularly probed and verified.
If a mirror is really down or compromised, jump into IRC: #mirror-admins and let them know.

---

### Post by Habitual on 2016-09-08
Expiration Date: 06-jul-2017

Does look a bit curious.

---

### Post by realmx2 on 2016-09-08
not browser hijack, according to this it's a legit mirror: [https://launchpad.net/ubuntu/+mirror/geekcdn-mirror](https://launchpad.net/ubuntu/+mirror/geekcdn-mirror)

When you go to it though it says it's not there, what's interesting is that the same page just says that the mirror was verified yesterday?!?

I'll jump in irc and let them know there, thanks everyone.

---

### Post by realmx2 on 2016-09-08
I can't figure out how to find the irc channel "#mirror-admins". I thought I joined it at freenode.net, but I guess not. Then I went to the launchpad group that @ian-weisser mentioned and tried to submit a bug, but it just keeps throwing me to a wiki on how to submit bugs. Very frustrating. Sorry if this is noobie stuff and you are all rolling your eyes right now, I just can't figure it out and it's getting more and more frustrating as I spend more time to figure it out.

Any advice, help, would be appreciated. I was just trying to be helpful.

---

