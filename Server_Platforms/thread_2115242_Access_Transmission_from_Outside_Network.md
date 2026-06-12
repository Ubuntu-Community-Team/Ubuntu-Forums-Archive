---
title: "Access Transmission from Outside Network"
date: 2013-02-12
forum: Server Platforms
---

### Post by Coniectoquisnam on 2013-02-12
I recently set up a 12.04.2 LTS Ubuntu Server (to use as a media server). I installed Transmission onto it, and it has been working fine while I am on the home network. My question is: How can I access it from outside my home network? I've done quite extensive googling but I'm sorry if this has already been posted. Thanks in advance for any responses.

---

### Post by darkod on 2013-02-12
You mean how to display the GUI interface when you are on a computer outside?

If you left it by default, I think the transmission GUI works on port 9091. So, all you will need to do is enter the configuration page of your home router, in the Port Forwarding section, and forward tcp port 9091 to the private IP of the server.

Then from the outside when you enter http://<public IP>:9091 it should show the GUI.

Note that if you have dynamic IP it can change over time. In that case you might consider some dynamic dns client, etc.

---

### Post by bubylou on 2013-02-12
Are you using a gui on your server. If not then i assume your using the transmission web ui which use port 9091. So just go into your router settings and forward that port for your servers ip. 

Also you may need to edit your transmission settings which is located in /var/lib/transmission-daemon/info/settings.json (i think) You will have to disable rpc-enabled and set it to false. Make sure aware of the risks involved in opening a service to the web and take the proper security measures.

---

### Post by darkod on 2013-02-12
Good call. I forgot about the transmission settings where you have to make sure it accepts connections. Usually it can be limited to the same internal network only, sometimes not even that, only from the localhost.

---

### Post by Coniectoquisnam on 2013-02-13
Thanks for all the help. Turns out that I had my port forwarding set up wrong, but it's all sorted now.

---

