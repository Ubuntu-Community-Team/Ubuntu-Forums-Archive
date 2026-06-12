---
title: "Can't login, but recovery mode works"
date: 2009-01-16
forum: Security
---

### Post by cariboo on 2009-01-16
I had something really strange happen this morning, I had a paper jam in my HP 5P laserjet, I logged into the cups adminstration app to clear the job, and got a message that I had to upgrade cups. I had just upgrade it a couple of days ago, so I couldn't see why I had to upgrade again. I tried to restart cups, but got a segfault.

The printer is located in my standalone garage, I was planning to do some work in the garage later on this afternoon, so I just left things as they were. I then started getting mail from the server about a Samba panic, so I sshed back into the server and got another segfault message when I tried to restart Samba. I logged out and tried to log back in again and got connection refused.

The next thing I tried was to ssh into another computer and then ssh into the server and again I got a connection refused message. This was getting a little frustrating, so I went out to the garage where the server is located and tried to login, and just kept getting the login prompt again. I restarted in recovery mode, and ran the usual checks to see if I could find out what happed. While at the root prompt, I created a new user and then continued booting to the login prompt, tried to login is the new user and was sent back to the login prompt again.

I need to access the shares on the server this afternoon, so I didn't spend any more time trying to find out what was wrong, and I am in the process of reinstalling as I write this. As a precaution, I have used a totally different 9 character password, as opposed to the 7 character password I was using.

Can anybody suggest what might have happed?

Jim

---

### Post by pdtpatrick on 2009-01-16
it's kinda confusing but i would think one of your services got hung up .. probably sshd or samba ... but then again it would have been helpful to check /var/log/messages to see what was going on .. if nothing else then restart sshd and samba .. see if that works. 

But since you are reinstalling, post again if this issue arises.

---

### Post by cariboo on 2009-01-16
I did check /var/log/messages and dmesg and saw nothing out of the ordinary. I did try restarting the services and got a segfault when trying to restart ssh, samba and proftpd.

Jim

---

