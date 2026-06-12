---
title: "Port Configuration for SkypeforLinux: Bionic-beaver"
date: 2018-10-04
forum: Security
---

### Post by skboseatg2d1 on 2018-10-04
For Video and audio transmission, please suggest the ports to open for udp and tcp . I have the latest skypeforlinux.

I have made 3478:3481/udp out , tcp 80,443 out.

What else is needed? 

Microsoft is unclear, and suggests a large number of ports to open. Unsure, opening all of them will make it work or not, at the cost of security.  

 Thanks Shamik

---

### Post by Claus7 on 2018-10-04
Hello,

forgive my ignorance, yet I do not think that aside installing it you need to do anything else. Are you sure that there isn't anything else that hinders its performance?

Regards!

---

### Post by skboseatg2d1 on 2018-10-04
Hello Claus7

It is about security and port configuration for skypeforlinux to work properly. Performance is not a concern. I tried earlier. The video transmission with my current setup is not happening. Thanks

---

### Post by Claus7 on 2018-10-04
Hello,

if your current setup is behind a specific configuration (firewall e.t.c.) then I do not think that I can help. 
If you are using 18.04 with skypeforlinux at a home computer, there is no need for you to change anything to your ports.
How have you installed skype? Which is your version? I would suggest you to install it via a deb file or launchpad and avoid snap.

When you have it running, can you click on the phone and video options? Are they available? Can you use camera and microphone with other applications? Have you run the test call of skype or it is completely blocked?

Some ideas,
Regards!

---

### Post by ajgreeny on 2018-10-04
Do you have a firewall running such as ufw which is blocking the usual skype ports?  I have to admit, I do not even know which ports are used.

I use Skype occasionally and it all works fine for both audio and video without any configuration being manually set.

---

### Post by skboseatg2d1 on 2018-10-04
Yes ufw is the firewall. If one makes no restriction for ports on out , then skypefor linux should run jolly-good. As I mentioned, I want only to open the necessary ports for udp/tcp so that outgoing video n audio transmission is fine. I gave port examples for udp and tcp at my original post which are open. It is not working properly. Video transmission is not happening. Thanks for your understanding.

---

### Post by Claus7 on 2018-10-05
Hello,

since its running ok without the ports closed, then you should narrow them down for your system. If this is the post that you are talking about: [https://support.skype.com/en/faq/FA148/which-ports-need-to-be-open-to-use-skype-for-windows-desktop](https://support.skype.com/en/faq/FA148/which-ports-need-to-be-open-to-use-skype-for-windows-desktop)

then you might not have other option, unless you configure your ports every time skype is used or try to narrow them down and see what you will get.

Regards!

---

