---
title: "Ubuntu One -- Can't Login"
date: 2009-08-12
forum: Ubuntu One (CLOSED)
---

### Post by brandoncolorado on 2009-08-12
I have Ubuntu One and I have logged in successfully multiple times.  Now, I am able to login, but when I click submit to send my openid info (it has my correct name and email), the page just refreshes. 

I have tries restarting, clearing cache, deleting cookies, and nothing has worked.

Any ideas?

---

### Post by beastrace91 on 2009-08-12
I am currently having the same issue - On Jaunty 64bit

~Jeff

---

### Post by andrea000 on 2009-08-12
I had the same problem with there web site but they
must have re did it because there is a new interface
and i can now log in to it.

---

### Post by Ryan Yo on 2009-10-07
Did this ever get resolved? I'm trying to login to Ubuntu One for the first time with my correct login info, but I just get redirected back to the login screen.

---

### Post by koma77 on 2009-10-07
I have the same problem: I keep getting redirected to the login screen.

---

### Post by jperez on 2009-10-08
Same here, but I have never logged into it.  I have a Launchpad account, but every time I said "Sign In" after showing the correct info, it won't let me.  Perhaps they are working on it?

Jesse~

---

### Post by KristinaK on 2009-10-09
same problem :(

---

### Post by Toolskyn on 2009-10-11
I guess it's some problem with the website, because I've got the same problem here.

---

### Post by HarmonicaGoldfish on 2009-10-11
Same thing was happening to me. I went directly to the site at [http://one.ubuntu.com]("http://one.ubuntu.com") and found I was already logged in. 

This might be a glitch with the url the software directs us to being the old url? Just a guess...

My software still does not connect though. Think I will do a reinstall and see if it works. Right now I use [dropbox]("https://www.getdropbox.com") for the same thing but I like the idea of sticking with ubuntu :)

---

### Post by HarmonicaGoldfish on 2009-10-11
ok. So once I realized I was logged in, I reinstalled the software. Then I clicked on 'connect', or it may have been 'go to web', and was brought to the one.ubuntu.com website where it asked if I wanted to register my computer. I did. It works just like dropbox. I drag files I want to share into my ubuntuone folder and it automatically uploads them to the server. 

Nice!

---

### Post by joshuahoover on 2009-10-15
> **Ryan Yo said:**
> Did this ever get resolved? I'm trying to login to Ubuntu One for the first time with my correct login info, but I just get redirected back to the login screen.

My apologies to all for the trouble with logging in. We're currently looking into this issue. It sounds like some here already had a subscription plan while others are new users trying to set things up for the first time. I've (personally) been able to reproduce the endless sign-in loop when I do not have a subscription plan (free or paid), but do not see this behavior now when I already have a subscription plan.

If you are having problems logging in and have a subscription plan, please report a bug by right-clicking on the Ubuntu One client applet and select "Report a Problem". Note that you have a subscription plan and the steps you're taking that gets you stuck in this sign-in loop.

For those without a subscription to Ubuntu One, the bug we're using to work/track this is: [https://bugs.edge.launchpad.net/ubuntuone-client/+bug/449842](https://bugs.edge.launchpad.net/ubuntuone-client/+bug/449842)

Thank you,

Joshua

---

### Post by jperez on 2009-10-16
I apparently don't have permission to access the bugs page on Launchpad...

I think I'll just not try UbuntuOne and instead go with something else like Dropbox as was mentioned earlier.  Thanks anyway...

Jesse~

---

### Post by Ryan Yo on 2009-10-16
> **joshuahoover said:**
> My apologies to all for the trouble with logging in. We're currently looking into this issue. It sounds like some here already had a subscription plan while others are new users trying to set things up for the first time. I've (personally) been able to reproduce the endless sign-in loop when I do not have a subscription plan (free or paid), but do not see this behavior now when I already have a subscription plan.

If you are having problems logging in and have a subscription plan, please report a bug by right-clicking on the Ubuntu One client applet and select "Report a Problem". Note that you have a subscription plan and the steps you're taking that gets you stuck in this sign-in loop.

For those without a subscription to Ubuntu One, the bug we're using to work/track this is: [https://bugs.edge.launchpad.net/ubuntuone-client/+bug/449842](https://bugs.edge.launchpad.net/ubuntuone-client/+bug/449842)

Thank you,

Joshua
Thanks for the reply. Glad to hear it's being tracked and I'm really looking forward to it getting cleared up. It's very annoying.

---

### Post by Ryan Yo on 2009-10-23
I just tried Ubuntu One again and everything seems to be in working order now. Sweet!

---

### Post by Wild_Duck66 on 2010-04-10
In Rhythmbox "an error has occurred with your request" If I "click here" for support I get system requirements which are Windows and Windows Media player (no Linux) and the "click here for support" at the bottom does not work.

---

### Post by joshuahoover on 2010-04-12
> **Wild_Duck66 said:**
> In Rhythmbox "an error has occurred with your request" If I "click here" for support I get system requirements which are Windows and Windows Media player (no Linux) and the "click here for support" at the bottom does not work.

It sounds like you're trying out the new Ubuntu One Music Store. If so, can you file a bug report here, following these instructions:

[LIST=1]
[*]File a new bug at: [https://bugs.launchpad.net/rhythmbox-ubuntuone-music-store/+filebug](https://bugs.launchpad.net/rhythmbox-ubuntuone-music-store/+filebug)
[*]Be sure to include the steps you took to get the error and the behavior you expected
[*]Let us know what version of the Ubuntu One Music Store you're using by running the following command in a terminal session (Applications->Accessories->Terminal) and pasting the output to the bug description: apt-cache policy rhythmbox-ubuntuone-music-store
[/LIST]
Thank you,

Joshua

---

### Post by Wild_Duck66 on 2010-04-18
Hi, I`ve done a clean install of Kubuntu 10.4 Beta 2 (even /home) and now it just will not connect to "Ubuntu one music store" when I proceed to "Checkout".
I`ve sent the results of "apt-cache policy" and "u1sdtool -s" to Launchpad.
Thanks for your help.

---

### Post by joshuahoover on 2010-04-19
> **Wild_Duck66 said:**
> Hi, I`ve done a clean install of Kubuntu 10.4 Beta 2 (even /home) and now it just will not connect to "Ubuntu one music store" when I proceed to "Checkout".
I`ve sent the results of "apt-cache policy" and "u1sdtool -s" to Launchpad.
Thanks for your help.

Thank you for the bug report! I replied to it here: [https://bugs.edge.launchpad.net/rhythmbox-ubuntuone-music-store/+bug/566296](https://bugs.edge.launchpad.net/rhythmbox-ubuntuone-music-store/+bug/566296) It looks like you need to try to connect to Ubuntu One. 

Thank you,

Joshua

---

