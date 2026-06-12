---
title: "Jack not working in realtime"
date: 2009-09-15
forum: Ubuntu Studio
---

### Post by g-raf on 2009-09-15
Qjackctl stopping working in the realtime setting. This is what happens after starting it up: 

 p, li { white-space: pre-wrap; }  cannot use real-time scheduling (FIFO at priority 10) [for thread -1211722048, from thread -1211722048] (1: Operation not permitted)
 cannot create engine
 [COLOR=#999999]15:11:00.850 JACK was stopped successfully.[/COLOR]
 [COLOR=#999999]15:11:00.851 Post-shutdown script...[/COLOR]
 [COLOR=#990099]15:11:00.851 killall jackd[/COLOR]
 jackd: no process killed
 [COLOR=#999999]15:11:01.259 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#FF0000]15:11:02.919 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]

I have Ubuntu Studio controls memlock set to 50%, nice at -10 and rtprio at 99. In the etc/security/limits.conf it's all "@audio". However, in the system>administration>"Users and Groups", there is no "audio" group that i can find. The only users are "username" and "root." Is that the problem?

---

### Post by dawiba on 2009-09-15
You need to make an audio group.

Go to System -> Administration -> Users and Groups

Click on 'Unlock'. Type in your password and click on 'Authenticate'

Next, click on the button 'Manage Groups'. Click on 'Add Group'

In the window that appears now, enter the word 'audio' in the Group Name field. Check the box beside your username in the bottom panel to make yourself a member of that group. Click 'OK'. If you use a firewire interface, you'll also need to create a video group. Enter the word 'video' in the Group Name field. Check the box beside your username in the bottom panel to make yourself a member of that group. Click 'OK'

Close all windows. Reboot for these changes to take effect. You will not be able to use these groups, which means you'll not be able to use Jack the way you want, until you have done so.

---

### Post by g-raf on 2009-09-17
Thanks. This fixed it right away.

---

### Post by mr.thraz on 2009-09-17
thx:)

---

