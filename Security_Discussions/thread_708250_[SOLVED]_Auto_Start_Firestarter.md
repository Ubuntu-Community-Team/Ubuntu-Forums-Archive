---
title: "[SOLVED] Auto Start Firestarter"
date: 2008-02-26
forum: Security Discussions
---

### Post by Xander {MP} on 2008-02-26
How do I add firestarter to services so that it automatically loads at start-up?


Thanks,

Xander {MP}

---

### Post by YldGuy on 2008-02-26
Preferences>Sessions>Add firestarter

---

### Post by hyperair on 2008-02-26
The firestarter service is automatically started up already. You can take a look at System->Administration->Services to confirm. The GUI for Firestarter... if you want it to be started up on boot, then you must add to your Sessions "gksudo firestarter". This will cause a password prompt upon every log in, so what you have to make an exception in the sudoers file:
```
sudo visudo
```

Add at the bottom:
```
<username> ALL = NOPASSWD: /usr/sbin/firestarter
```
Replace <username> with your username.

---

### Post by bodhi.zazen on 2008-02-26
I advise you NOT run firestarter this way. Firestarter is a gui tool used to configure your firewall, iptables.

Your firewall remains active if you close the Firestarter GUI interface, including a reboot.

firestarter runs as root and is thus a security risk, and editing /etc/sudoers to allow it to run without a password makes matters worse.

You should NOT run firestarter all the time (unlike windows firewalls) and you should NOT use it to monitor your network, doing either is a common fallacy.

[https://help.ubuntu.com/community/Firestarter](https://help.ubuntu.com/community/Firestarter)

---

### Post by Xander {MP} on 2008-02-27
Ok cool. On a different note how can I monitor my wireless network? My roomates mac lets him see who is on. Is there anything like that in the repositories.


Thx,

Xander {MP}

---

### Post by jaygo on 2008-02-28
synaptic > search > wireless (name & description
This turns up a lot of stuff. I haven't used any of it but it looks like netdiscover, among others, does what you're looking for.

---

### Post by raydar on 2008-03-29
I just installed Firestarter, to test it out in order to make a recommendation to a friend.  I found that when I boot up, I have no web access until I run the Firestarter app.  If the Firestarter app is just a GUI for something already running, then I wonder why it has this effect, 'cause I don't have to change anything to get my internet to work again; just run the app.

I was disappointed to find that un-installing Firestarter did not give me back automatic internet access upon boot; apparently I have to figure out what to change in my iptables if I want to get that back. :(   So re-installed Firestarter for the time being.  Anybody have a silver bullet for getting my internet access back without continuing to use Firestarter?

Thanks for any help!

--Ray

---

### Post by nvteighen on 2008-03-29
I've written a How-To on this matter. See my sig.

---

### Post by raydar on 2008-03-29
Thanks, nvteighen.  I followed the instructions there; my machine exhibited the problem behavior described there.  After changing the firestarter.sh file and rebooting, I verified that the "sudo iptables -nL" output had changed, and I looked at the output again after I ran the Firestarter app to see that it was the same, and as far as I can tell, it was.  

But I still have no internet until I run the Firestarter application. I can repeat it over and over: (1) Reboot, (2) start Firefox and get "Problem loading page" on every tab, (3) start Firestarter, (4) hit refresh on a Firefox tab and see the web page load.

How strange.  Any further ideas?

---

### Post by cdenley on 2008-03-31
I'm not sure why your firestarter init script isn't working, but if you want to remove firestarter completely, you can run
```

sudo dpkg -P firestarter

```
You don't really need a firewall unless you installed server software that shouldn't be world-accessible and haven't configured it properly.

What was the output of "sudo iptables -nL" when your internet wasn't working?

---

### Post by raydar on 2008-03-31
Aha!  To answer your question with a quote, it was (in part) the below--the line under "target" being one I missed the first time I compared files, when I was looking for differences in all the IP addresses & categories in the main part of the file: 

Chain INPUT (policy DROP)
target     prot opt source               destination         
moblock_in  0    --  0.0.0.0/0            0.0.0.0/0           state NEW MARK match !0x14 

All I had to do was open MoBlock--the other app I was testing out for the same friend--and after restarting I had an internet connection just fine.  

I thought I read something warning that those two apps don't always get along, and evidently Firestarter, when running, removes the MoBlock line from the top of the iptables data.  So when I removed Firestarter, it's not that it had left my iptables messed up; rather, MoBlock was left able to un-internet me.

So my problem's solved, and it looks like I don't even need to move to another thread, 'cause all I had to do to get MoBlock to let me online was enable outgoing http & https in the Mobloquer GUI's settings (oughtn't those, even if only those, be on by default? oh well!).  :)

But your question, cdenley, brings up another question: I wound up not posting my whole iptables output here mostly 'cause I found the solution first; but it also occurred to me to wonder whether that data would be harvestable by some bot fishing for ways into networks & machines.  I'm sure no expert; anyone know how safe that is/isn't?

---

