---
title: "Authorization Error"
date: 2009-10-31
forum: Ubuntu One (CLOSED)
---

### Post by Grozzy on 2009-10-31
Hi all!

I have never tried Ubuntu One and I though I could try it now when it comes with Ubuntu 9.10.

Well, I can't eaven start it :P
When I click Applications > Internet > Ubuntu One a popup shows me this:

Authorization Error
Error showing url: Failed to execute child process "/home/pontus/Desktop/firefox/firefox" (No such file or directory)

Everytime I try to do something with Ubuntu One, that pop up.
My dad is having exactly the same problem on his computer.

Maby I just should wait for an update to fix the problem or can I fix it?

// Grozzy

---

### Post by joshuahoover on 2009-11-02
> **Grozzy said:**
> Hi all!

I have never tried Ubuntu One and I though I could try it now when it comes with Ubuntu 9.10.

Well, I can't eaven start it :P
When I click Applications > Internet > Ubuntu One a popup shows me this:

Authorization Error
Error showing url: Failed to execute child process "/home/pontus/Desktop/firefox/firefox" (No such file or directory)

Everytime I try to do something with Ubuntu One, that pop up.
My dad is having exactly the same problem on his computer.

Maby I just should wait for an update to fix the problem or can I fix it?

// Grozzy

Hi Grozzy,

One thing I will ask you to do is to check System->Preferences->Preferred Applications and see what your web browser is set to there. It should be set to Firefox, but maybe it's set to a custom command? Also, try running this command in a terminal session: gnome-open [https://one.ubuntu.com](https://one.ubuntu.com)

I haven't heard of anyone having this problem before. Can you right-click on the Ubuntu One client and select "Report a Problem". This will file a bug report and include some config details that will help us figure out the root cause of this problem. Please include the details that you provided here as well as what you found from checking things out I requested above.

Thank you,

Joshua

---

### Post by Grozzy on 2009-11-02
> **joshuahoover said:**
> Hi Grozzy,

One thing I will ask you to do is to check System->Preferences->Preferred Applications and see what your web browser is set to there. It should be set to Firefox, but maybe it's set to a custom command? Also, try running this command in a terminal session: gnome-open [https://one.ubuntu.com](https://one.ubuntu.com)

I haven't heard of anyone having this problem before. Can you right-click on the Ubuntu One client and select "Report a Problem". This will file a bug report and include some config details that will help us figure out the root cause of this problem. Please include the details that you provided here as well as what you found from checking things out I requested above.

Thank you,

Joshua

Ha! 1000 thanks Joshua, it works now!
The problem was that my default webbrowser was set to "custom" as you said, I did just change it to Firefox.

Enjoying Ubuntu One! =D>

---

### Post by Robertjm on 2010-05-11
Joshua,

Just wanted to say "THANKS" for the quick answer you gave to the OP on how to fix this problem. I had the same problem today and you're was the first post I found when I searched the web on how to fix it!!

Robert

---

### Post by webliner1023 on 2010-09-16
Hello all,

Im having a different problem. Everytime I try to connect to Ubuntu One a pop appears saying:

> Authorization Error

[Errno socket error] [Errno 1] _ssl.c:48...GET_SERVER_HELLO:unknown protocol

Is it a problem related to my network connection? I connect to the internet through my Institute proxy. 

Could anyone help me in this please!

---

### Post by duanedesign on 2010-09-19
Unfortunately at the moment Ubuntu One does not support proxies. Ubuntu One will support proxies in Maverick 10.10. 

thank you,
duanedesign

---

### Post by tgrego on 2011-10-07
I know this is an old thread, but I have exactly the same problem as webliner1023...

I try to run ubuntu one and I get:

> 
Authorization Error

[Errno socket error] [Errno 1] _ssl.c:48...GET_SERVER_HELLO:unknown protocol 


I'm using Ubuntu Lucid, with ubuntuone-client v1.2.2-0ubuntu2
Is ubuntu one supporting proxies already somehow? do I have to install some specific Maverick/Natty/Oneiric packages?

thanks

---

