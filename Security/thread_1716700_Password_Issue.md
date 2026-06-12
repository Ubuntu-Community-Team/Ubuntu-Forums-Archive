---
title: "Password Issue"
date: 2011-03-28
forum: Security
---

### Post by freakinjonathan on 2011-03-28
How can I setup Ubuntu so that it requires a password to access the Internet? This is after I login with my password, I will have to fill out my password again to access the Internet?

---

### Post by dacoolio on 2011-03-29
I don't know about you, but when I set up my keychain containing my wireless password, I need to enter the keychain password to enable wireless. If you are using wifi, I'd look into this.

---

### Post by freakinjonathan on 2011-03-30
Thanks, I am looking for exactly that, but with networking in general, not just wifi. Any ideas? 
I guess I could restrict the networking service from starting and then have to enter my password after login for that?

I want to have the workstation accessible by auto login but prevent unauthorized access to the internet.

---

### Post by BkkBonanza on 2011-03-30
If you don't need network access for a LAN then your simplest way may be to do as you suggest and disable the networking at boot. Then create a desktop/menu shortcut so it's easy to enable it manually. That will prompt for your password. I haven't tested this but you should be able to have a shortcut that just calls a command like,

**gksu start networking**

A traditional way of controlling internet access for a netowrk is with **captive portal** software. So if you need something more extensive you may want to investigate that. Some routers have it built in as an option but that would depend on how you are setup for the net. 

Disabling your networking won't stop someone from poping the cable into their own machine though. For that you would need a captive portal or some type of proxy with authentication.

---

### Post by freakinjonathan on 2011-04-01
@BkkBonanza Thanks that sounds like a good solution! So where is the list of services that load on boot located?

Thanks.

---

### Post by BkkBonanza on 2011-04-01
If you use NetworkManager see this page, far down about disabling.

[https://help.ubuntu.com/community/NetworkManager](https://help.ubuntu.com/community/NetworkManager)
(that page is old but I couldn't find similar info on newer pages)

I don't use NetworkManager so can't check here how that works or not. Then presumably you can start it manually with,

sudo start NetworkManager

though I'm not sure about that. It may only work with,

sudo /etc/init.d/NetworkManager start

---

### Post by Duncan Williams on 2011-04-02
You can setup a proxy:
say at [fastun]("http://fastun.com/")
Then when you have finished your session you can switch your browser to `use proxy'

This will then require a password to access web pages.

When you return to your session you can switch the proxy off (or login to use it)

---

