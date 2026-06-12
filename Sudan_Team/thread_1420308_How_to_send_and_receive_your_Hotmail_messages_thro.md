---
title: "How to send and receive your Hotmail messages through Evolution in karmic"
date: 2010-03-02
forum: Sudan Team
---

### Post by zero-n on 2010-03-02
I have face a trouble night until i found the solution, so what you need to do is following these step it work for me for both sending and receiving:

1- Open Evolution ;)

2- go to **Edit **>>** Preferences** >>** Mail Accounts **>> **Add **

3- Type your **Name** and the **full email address** ( [EMAIL="xxx@yyy.com"]xxx@yyy.com[/EMAIL] ) and click **Forward**

4- At the **Receiving Email** window do the following 
       **Server Type :** POP
       **Server :** pop3.live.com:995
       **Username :** You full email
       **Security:** SSH encryption
      ** Authentication type:** Password

and click forward.

5- At the **Receiving Options** window slect what you prefer and click forward.

6- At the **Sending Options** window do the following
       **Server Type :** SMTP
       **Server :** smtp.live.com:587
       **Server requires authentication :** checked
       **Security :** TLS
       **Authentication :** PLAIN or Login
       **Username :** Your full username

and click forward.

7- Select a name for your account.

8- Forward , Apply & done.


Finally you can press the send/receive button to manually check your email.

Thanks to Ubuntu [[COLOR=Red]**community**[/COLOR]]("https://help.ubuntu.com/community/UsingHotmailWithEvolution").

---

