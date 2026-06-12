---
title: "sourceforge login problems"
date: 2010-04-15
forum: The Cafe
---

### Post by cong06 on 2010-04-15
I can't think of anyplace else to ask about this... but the Ubuntuforum seems a reasonable place to ask.

I'm on a slow, unstable internet connection, and maybe this is the reason for my problem.
I've been trying to log into sourceforge over the last several days, and each time I log in, it loads...loads... and finally redirects me to the page where I clicked "login"
But I'm still a guest.

Occasionally it will log me in, but as soon as I refresh, it logs me out.

This happens with Google chrome and firefox.
With Chrome I have the cookies set to "Allow"
and Firefox 3.5: "Remember History" (which as far as I can tell saves cookies)

I have no problem with ubuntuforums.org, google.com, linuxquestions.org

---

### Post by lovinglinux on 2010-04-15
This happens to me sometimes on Ubuntu forums, when opening a page from the RSS reader without being logged. When I log in, the forum redirects me to the main forum page. When I try to go back, it doesn't recognize me as logged in, even if I reload the original post page. I'm not sure exactly why this happens. Try to delete Firefox cache and cookies if you can, then login again and make sure you select the "Remember Me" option in SF site.

---

### Post by cong06 on 2010-04-15
With both, Chrome and Firefox, I clicked the "Remember Me"

That being said, I tried what you mentioned, and it didn't work.
No errors, just simple not logging in.

---

### Post by lovinglinux on 2010-04-15
See [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://lovinglinux.megabyet.net/?page_id=220#General-Troubleshooting-Steps-2) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by cong06 on 2010-04-15
I checked out your FAQ.
I created a new profile, and even with this new profile I had problems.

I logged in. I accepted, logged me in, showed my name in the top right corner.
Then I decided to run a search for software.
Immediately on showing the next page it logged out, even when "Remember me" was used.

The fact that firefox and chrome are BOTH having this problem makes me think it's bigger then the browser.

I have two networks set up, one with a dial up modem that goes to a squid cache server, the other one just a modem.
At first I thought it was the squid proxy, but since I tried it without the modem, and had the same effect, I can only guess that it's the fact that the network is unstable...

Anyway, I guess I'm on my own on this one. I'll just have to not use sourceforge.net

---

### Post by lovinglinux on 2010-04-15
You could try to create a new Ubuntu user and see if you can login from there, so you would be able to determine if the problem is some Gnome settings.

---

### Post by cong06 on 2010-05-06
I was convinced that it wasn't my transparent squid proxy, but after a clean reinstall, I'm forced to admit it must have been a software problem on my end. (as opposed to a network problem)

Now I have it working again.

---

