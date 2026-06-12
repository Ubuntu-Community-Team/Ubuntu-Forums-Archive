---
title: "Firewall"
date: 2009-05-22
forum: Security
---

### Post by rishabh_destiny on 2009-05-22
How to install a firewall in jaunty?? I'm completely new to it. Plz provide detailed steps. Thnx

---

### Post by zja on 2009-05-22
a. Applications > Add/Remove...
b. serach for Firestarter
c. install...
d. Applications > Internet > Firestarter
e. enter password
f. DONE!

have fun :P

---

### Post by Kevbert on 2009-05-22
Rather than install a new firewall why not use Uncomplicated Firewall, it's installed by default and documentation is [[COLOR="Red"]here[/COLOR]]("https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw").

---

### Post by bodhi.zazen on 2009-05-22
firestarter is depreciated and often conflicts with ufw if installed.

If you advise firestarter, at least remove ufw.

IMO better to use ufw. If you want a gui front end, use gufw (gufw is in the repositories).

---

### Post by heffo_j on 2009-05-22
Open Synaptic, search for and install Gufw. It will show up in your Administration folder.

Regards
John

---

### Post by lovinglinux on 2009-05-22
**Installation**

[list][*] Applications > Add/Remove...
[*] Search for gufw
[*] Select the application called "Firewall Configuration"
[*] Click "Apply"[/list]

**Configuration**

[list][*] Go to "System > Administration > Firewall Configuration"[/list]

Once you configure it, you can close the firewall gui.

As bodhi.zazen explained, Firestarter is not recommended anymore. Also keep in mind that both Firestarter and GUFW are just firewall managers, which are tools that allow you to create firewall rules without knowing the iptables (the real firewall) commands.

---

### Post by rishabh_destiny on 2009-05-23
But these are only firewall managers. I want to monitor what ip address do my browser connect to and which ip address i'm chatting with in pidgin. How to achieve this?

---

### Post by lovinglinux on 2009-05-23
> **rishabh_destiny said:**
> But these are only firewall managers. I want to monitor what ip address do my browser connect to and which ip address i'm chatting with in pidgin. How to achieve this?

Install IPTState

```
sudo apt-get install iptstate
```

It's command-line only, but very nice. 

[IMG]http://sourceforge.net/dbimage.php?id=92392[/IMG]

---

### Post by rishabh_destiny on 2009-05-23
For Command line, i have to learn a lot. Any GUI?

---

### Post by lovinglinux on 2009-05-23
> **rishabh_destiny said:**
> For Command line, i have to learn a lot. Any GUI?

Actually, there is nothing to learn about it. It's pretty simply. You should try it. The only command you need is the one to start the program:

```
sudo iptstate
```

All the rest is done through the keyboard. Once you are running the program in the terminal, hit "h" to see the list of available short keys.

---

### Post by albinootje on 2009-05-23
> **rishabh_destiny said:**
> For Command line, i have to learn a lot. Any GUI?

You can install and use "wireshark" to monitor your traffic.

---

### Post by lovinglinux on 2009-05-23
> **albinootje said:**
> You can install and use "wireshark" to monitor your traffic.

Isn't it kind of an overkill, specially for a newcomer?

---

### Post by albinootje on 2009-05-23
> **lovinglinux said:**
> Isn't it kind of an overkill, specially for a newcomer?

Perhaps, but the OP asked for it ;-)

I can't think of any other GUI which shows the network traffic, and 
can filter it. And I don't know any GUI firewall-management software for Linux which can do what the OP asks for.

---

### Post by rishabh_destiny on 2009-06-01
I'v installed firestarter. But it keeps on telling that hits are received from port 445 that's Microsoft ds. Any clue, what the hell is microsoft thing doin in ubuntu?

---

### Post by lovinglinux on 2009-06-01
> **rishabh_destiny said:**
> I'v installed firestarter. But it keeps on telling that hits are received from port 445 that's Microsoft ds. Any clue, what the hell is microsoft thing doin in ubuntu?

Firestarter is not good for monitoring connections because it actually doesn't know what service is connecting. It makes a wild guess based on standard ports. For example, if you use a torrent client on port 25, it will tell you that it is an SMTP connection (mail), because it's the standard service that uses this port, not torrent.

Anyway, the connection on port 445 is probably Samba. Do you have Windows machines on your network? Did you configured shared folders with a Windows machine?

---

### Post by ianmillington on 2009-06-01
I've just installed UNR 9.04 on my wifes netbook, removing linpus as, being familiar with kubuntu, I felt it would be fairly easy for me to maintain it for her, as it's her first ever computer. Having now got it nicely set up, I need to give some thought to security.

I know there is the perennial question about firewalls (and anti-virus) in linux. I have done a "shields up" test and all common ports are returned as stealthed, with the exception of SSH which is shown as "closed" (I believe this to be due to my enabling the firewall at my ISP as all computers I connect exhibit this). Does it need anything else? I'm thinking user friendly here. My experience with guarddog was that configuring it disables everything that I had not enabled - I remember being puzzled as to why I could not send an e-mail with thunderbird until specifically enabling SMTP. However by analogy does enabling a service by opening the appropriate port then simply open the system to outside influence or is it just for outbound use?

The principle things the netbook will be used for are browsing (including Youtube etc) Gmail (possibly via IMAP)document production etc. She might also take it with her when we go on holiday as the hotel has wifi. I want to "set and forget" it. I don't think messages flashing from the taskbar (as with Zone Alarm for example)will be particularly helpful. My initial thoughts are I should go with what I know (Guarddog) or maybe nothing at all might be better. Any thoughts on this folks?

Thanks

ian

---

### Post by brian_p on 2009-06-01
> **ianmillington said:**
> 

. . . . .  or maybe nothing at all might be better. Any thoughts on this folks?

Doing more than nothing is overkill. Your newly installed OS has no services running which can be accessed from the internet. For your intended use you do not appear to need to install any either.

---

### Post by koenn on 2009-06-01
> **lovinglinux said:**
> Install IPTState

```
sudo apt-get install iptstate
```

It's command-line only, but very nice. 


I've got a launcher on my panel that does 
```
xterm -T "connections" -bg black -fg green -geometry 90x25 -e watch -n1 netstat --inet -an
```
it's basically netstat with a 1 second refresh
When it runs, there's a window border around it with min/max/close buttons, so it must be GUI  ;)

---

### Post by rishabh_destiny on 2009-06-01
Reply me in simple words. which firewall should i use if not firestarter. It should have a gui like firestarter cos i'm not so comfortable with the command line

---

### Post by albinootje on 2009-06-01
> **ianmillington said:**
>  I want to "set and forget" it.

gufw is simple and efficient. I like it very much.
It's included in Intrepid and Jaunty, and Hardy backports.

After installation it's under -> System -> Administration

Screenshots here : [http://gufw.tuxfamily.org/screenshots.html](http://gufw.tuxfamily.org/screenshots.html)

---

### Post by rishabh_destiny on 2009-06-01
I've installed it. But it's not showing any connections

---

### Post by albinootje on 2009-06-01
> **rishabh_destiny said:**
> I've installed it. But it's not showing any connections

Choose "deny incoming traffic", and then open the ports that you need.
If you want to see what happens, check the log files, or use iptstate, or iptraf or something like that.

---

### Post by rishabh_destiny on 2009-06-01
> **albinootje said:**
> Choose "deny incoming traffic", and then open the ports that you need.


I have to enter every port MANUALLY?? That will be a nightmare... I just want to monitor my traffic. Closing ports will be more easier that opening every single port manually

---

### Post by lovinglinux on 2009-06-01
> **rishabh_destiny said:**
> I have to enter every port MANUALLY?? That will be a nightmare... I just want to monitor my traffic. Closing ports will be more easier that opening every single port manually

Gufw does not block outgoing connections, so you won't have to open any port for web browsing, receiving e-mails and such. You only need to open ports for incoming connections if you use programs that require an open port for accepting incoming connections (like p2p programs). So, denying all incoming traffic and opening just the ports you need is the easiest and safest way to setup the firewall. I don't understand what you are trying to achieve. How many ports you need to open for incoming connections?

Gufw is not a monitoring tool. If you wan to monitor connections then use [this](http://ubuntuforums.org/showpost.php?p=7381615&postcount=18) or [this](http://ubuntuforums.org/showthread.php?p=7331295#post7331295). I understand you are not comfortable about using command-line, but as I said, using iptstate is not complicated at all. All you have to do is launch it from the terminal. Then you can do basic stuff like sorting the connections with keyboard shortcut, by typing "b" or "h" for help. 

You can also create a launcher in your panel to launch iptstate. Right-click on the panel, then select "Add to Panel", then select "Custom Launcher Application", then select "Application in Terminal" from the drop-down list, then give it a name and put **sudo iptstate** in the command field. Click OK and you will have a launcher.


If you want to monitor blocked connections, then open the terminal and type 

```
tail -f /var/log/messages.log | grep [color=#FF0000]eth0[/color]
```

Where [color=#FF0000]eth0[/color] should be replaced with your network device.

If you still think this is too complicated, then stick with Firestarter. But I don't recommend running it all the time just to monitor connections, due to security risks.

---

### Post by lisati on 2009-06-01
> **rishabh_destiny said:**
> Reply me in simple words. which firewall should i use if not firestarter. It should have a gui like firestarter cos i'm not so comfortable with the command line

Ubuntu comes with a firewall called *iptables* - what firestarter, ufw and other software mentioned by the other posters do is help you manage the settings for iptables (it can be a bit baffling for a newcomer to set it manually) or to show you what's happening on your network.

---

