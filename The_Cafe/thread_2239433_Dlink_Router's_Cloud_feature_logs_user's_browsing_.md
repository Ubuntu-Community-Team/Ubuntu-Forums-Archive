---
title: "Dlink Router's Cloud feature logs user's browsing !"
date: 2014-08-13
forum: The Cafe
---

### Post by linuxyogi on 2014-08-13
Hi,

I purchased [this router]("http://www.dlink.co.in/products/?pid=544") recently. This is first time I am using a Wi-Fi router so I am a bit worried about security. This Dlink router has a cloud feature which enables users to view the status, monitor the network like who is connected and make some configuration changes remotely. This does not require opening the WAN interface to the Internet.

By default this feature is not  enabled. One needs go to the admin page to create an account. There are three options to access the account. The first is using dlink's phone app, the second is using their app for PC which is available only for Windows and Mac and the third is by visiting [https://sg.mydlink.com](https://sg.mydlink.com) .

The main reason I registered for this service is because I want to receive an alert if an unauthorized device connects to my network.

[IMG]http://ibin.co/1Wk1DJGeg5Ey[/IMG]

^^ As you can see I have enabled that feature but the problem is while browsing the web interface I found that Dlink is actually keeping logs of all websites visited by devices 

connected to my network.


[IMG]http://ibin.co/1Wk2BsctJZxt[/IMG]

I searched but didn't find any option to disable this feature. I guess nothing can be done I am just sharing this with you guys. 

So the bottom line is if someone wants to receive alerts about intrusions he is forced to give away the browsing data of his entire network to Dlink ! =d>

---

### Post by tgalati4 on 2014-08-14
You might be able to install another firmware such at tomato or dd-wrt and make the router do what you want.  If you have another machine running 24/7 (such as a server) then you could probably set up *rsyslog* and a script to monitor your connections and send an email or text when an intrusion occurs.  Routers are not secure, nor are your modems that you use to get internet.

---

### Post by linuxyogi on 2014-08-14
I visited the dd-wrt and tomato websites but unfortunately my router is not supported.

I got only one PC atm but I am planning to buy an Android phone next month. I will try and find out if the phone can do this for me.

---

