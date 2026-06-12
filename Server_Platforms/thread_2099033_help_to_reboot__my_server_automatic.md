---
title: "help to reboot  my server automatic"
date: 2012-12-28
forum: Server Platforms
---

### Post by bario22 on 2012-12-28
hi freinds,
is it possible to reboot my server every 9 hours automatic ?
i have server ubuntu 11.04 
i dont know how to do it
please help
thanks

---

### Post by Cheesemill on 2012-12-28
One way to achieve this would be to add the following line to your /etc/rc.local file (before the exit line). Anything in rc.local gets run with root privileges every time the system boots.

```
shutdown -r +540
```Can I ask why you want your server to reboot every 9 hours?
Also did you know that 11.04 is now unsupported and doesn't receive bug fixes and security updates anymore.

---

### Post by bario22 on 2012-12-28
first thanks for reply
my server freez almost every 9 hour, after restart it work good :(
thats why i need automatic reboot every 9 hour
can you tell me what ununtu is good to use 
thanks

---

### Post by Lars Noodén on 2012-12-28
For servers, it is always good to use the Long Term Support (LTS) version.  That would be 12.04 LTS.  

But rather than restarting the server, it would be good to get to the bottom of why it is locking up.  What do the logs say?  Take a look in /var/log/syslog at timestamps leading up to the lock up.

---

### Post by Cheesemill on 2012-12-28
You should figure out *why* your server is freezing every 9 hours instead of just automatically rebooting it.

If you can I would suggest installing Ubuntu Server 12.04.1 as it is the newest LTS (long term support) release. This means it is supported until 2017 so you wont have to upgrade again for 5 years.

You may also find that by installing 12.04.1 and setting up your services from scratch that you fix your current freezing issue.

[http://www.ubuntu.com/download/server](http://www.ubuntu.com/download/server)

---

### Post by bario22 on 2012-12-28
thanks eveybody for help
i will try it today.
happy new years

---

### Post by bario22 on 2012-12-28
One way to achieve this would be to add the following line to your /etc/rc.local file (before the exit line). Anything in rc.local gets run with root privileges every time the system boots.


Code:
shutdown -r +540
its not possible to save the line in rc.local
what is the probleme?
i do exactelly what you say to me

---

### Post by darkod on 2012-12-28
That is a system file and you need to open it with sudo permissions to edit it. I don't know which editor you are using. You can try:
sudo nano /etc/rc.local

---

### Post by CharlesA on 2012-12-28
> **Lars Noodén said:**
> For servers, it is always good to use the Long Term Support (LTS) version.  That would be 12.04 LTS. 

Agreed. I would not use anything other than a LTS release on a production box (or test box for that matter..). 

> But rather than restarting the server, it would be good to get to the bottom of why it is locking up.  What do the logs say?  Take a look in /var/log/syslog at timestamps leading up to the lock up.

Agreed. It might help to also hook up a monitor to the box if it is running headless and seeing if there is any output to the screen that shows a kernel panic or something.

> **Cheesemill said:**
> You should figure out *why* your server is freezing every 9 hours instead of just automatically rebooting it.

If you can I would suggest installing Ubuntu Server 12.04.1 as it is the newest LTS (long term support) release. This means it is supported until 2017 so you wont have to upgrade again for 5 years.

You may also find that by installing 12.04.1 and setting up your services from scratch that you fix your current freezing issue.

[http://www.ubuntu.com/download/server](http://www.ubuntu.com/download/server)

+1.

I don't really think there is much to add other than tracking down the problem and/or installing a LTS release.

---

### Post by bario22 on 2012-12-28
thanks darkod, its working.
i will do what all freinds says: LTS

---

### Post by darkod on 2012-12-28
I don't understand your PM. And please post here instead of sending PMs because other people may see your question and comment too.

You say in the last post that it's working, but then in the PM that you can't see the edited line in rc.local after you restart. If the line is not there, it would not be working.

Anyway, the line you add to rc.local should be there. You don't change the filename, you only edit it and save with the changes. The filename stays the same, that's the point.

Maybe you don't know how to save with nano, as I said it depends which editor are you comfortable using. On a server I use nano. When you are done editing the file in nano, to save it with the same name you press Ctrl+O, Enter.
Then to close nano you press Ctrl+X.

That's it. The file will be saved with the same name, and it will include the changes you did.

---

### Post by bario22 on 2012-12-28
yeah sorry to send pm, im new to this forum
i feel shame but thats how we learn .
yes i have nano and i made mistak when i save the file.
now its good after restart and shec.
my respect

---

