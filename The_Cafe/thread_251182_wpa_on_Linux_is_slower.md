---
title: "wpa on Linux is slower?"
date: 2006-09-05
forum: The Cafe
---

### Post by Sunnz on 2006-09-05
Anyone use wpa_supplicant for wireless networking here?

Well I have been putting all my movies on a central samba server so I don't have a duplicate copy on every computer...

However, I find that when playing movies on my Mac (OSX 10.4.7) it is as if the movies are still on my computer, whereas on Linux, it feels like streaming - short pauses every 10 ~ 20 seconds.

The movies are still viewable on Linux, just not as good as on OSX... is this because of wpa?

---

### Post by wieman01 on 2006-09-05
This is probably because of SAMBA, not WPA. WPA (incl. WPA2) work fine on Linux, I have not noticed any performance issues. SAMBA, however, turned out to be a bit slow.

You don't have a choice since you need to connect to a MAC computer, but in my case I could turn it off and use NFS instead as I am LINUX only. :-)

---

### Post by Sunnz on 2006-09-05
If it is Samba then why it works so flawlessly on OSX? Is it the Samba client that makes it slow? But OSX is using the same Samba client I think...

I was thinking about NFS too... but Samba had more documentaion so it turns out to be easier to setup... and I might have Windows friends who I might want them to access the server in the future.

---

### Post by wieman01 on 2006-09-05
No idea why it's alright on the MAC. Actually, now that I think about it, I have actually never had performance issues with SAMBA, either. Not even in a Linux environment with WPA2 enabled. 

Beats me why it's so slow. Have you got a firewall?

---

### Post by Sunnz on 2006-09-05
Well it is not like "unbelievably" slow... just a few very short and "somewhat acceptable" pauses when playing movies...

BTW, when playing small movies, I have been playing the movie to the end, then without quitting the playing software, rewind it to the very beginning, and then it plays flawlessly just like the Mac... maybe it could be the software that is used to play the movie? (Mplayer vs. Quicktime.)

Firewall... well the router has a hardware firewall, but that doesn't have anything to do with the LAN, right? The Linux box that is playing the movie has no firewall AFAIK of.

BTW, when you said you have no performance issue with Samba... but what were you doing? Were you playing movies or?

---

### Post by wieman01 on 2006-09-05
I was playing DIVX movies and such. So pretty much the stuff you are doing. I am normally using Kaffeine or Xine to play movies without problems. Could you try these and compare?

Your router's firewall does not play a role indeed. 

Is the router very far apart from your computers? I figured that to be a problem sometimes, in particular when I close doors, etc.

---

### Post by Sunnz on 2006-09-05
> 
Is the router very far apart from your computers? I figured that to be a problem sometimes, in particular when I close doors, etc.

The server is directly connected to the router on a network cable... however both my Mac and Linux are connected wirelessly... I tested them at the same distance though.

> **wieman01 said:**
> I was playing DIVX movies and such. So pretty much the stuff you are doing. I am normally using Kaffeine or Xine to play movies without problems. Could you try these and compare?Ok I'll guess I'll try them out...

---

### Post by wieman01 on 2006-09-05
Could really be the software you are using (Quicktime). Perhaps their caching process is just poor. Try out the other applications I have mentioned and let us know how it goes. If you still have issues, we'll think of some other solution.

---

### Post by prizrak on 2006-09-05
Could be a hardware issue, I stream movies over SAMBA with wi-fi and WPA all the time and have no issue. NFS is very easy to setup but is 100% manual there is no nice automation for it in Gnome. Your Mac box should be able to run it. Could also be a driver, what WNIC are you using in the Ubuntu box?

---

### Post by Sunnz on 2006-09-05
The Linux box is using Madwifi...

I did set-up Samba by hand... the Samba server doesn't have X installed... in fact is has no monitor.

---

### Post by prizrak on 2006-09-05
Madwifi could be your issue. I got a machine with that, it seems a bit iffy at times. For instance my signal stregth does not go above 80% even if I'm 2 feet from the router.

---

