---
title: "I think someone opened a backdoor to my computer"
date: 2011-11-26
forum: Security
---

### Post by MegaTopx on 2011-11-26
I'm feeling insecure, and I need help. Is there anyway that I might be able to detect if someone is spying on me through a backdoor? Through the terminal, perhaps on an Ubuntu 10.04.3 LTS computer.

Any help would be greatly appreciated.

---

### Post by CryptAck on 2011-11-26
Check for open ports on your computer. Ideally you don't want ports open that you aren't using. 

Take a look at your running processes/applications; ensure that they are what you expect.

---

### Post by bluexrider on 2011-11-26
Are you running a firewall and are you using a router? Either one should stop an intruder if configured correctly.

---

### Post by MegaTopx on 2011-11-26
Is  sudo netstat -anltp|grep :80 the only way to check for backdoors? Could anything be hidden?

My results were:

tcp        0      0 [MY_IP]:46606      74.125.225.40:80        ESTABLISHED 1616/firefox-bin
tcp        0      0 [MY_IP]:46224      74.125.225.51:80        ESTABLISHED 1616/firefox-bin
tcp        1      0 [MY_IP]:38450      91.189.89.31:80         CLOSE_WAIT  2388/gvfsd-http 
tcp        0      0 [MY_IP]:40579      74.125.225.60:80        ESTABLISHED 1616/firefox-bin

and I did again right after, my results were:

tcp        1      0 [MY_IP]:38450      91.189.89.31:80         CLOSE_WAIT  2388/gvfsd-http 
tcp        0      0 [MY_IP]:40579      74.125.225.60:80        ESTABLISHED 1616/firefox-bin

And how would I configure a router or firewall? Would it be too late if there was already an intruder?

---

### Post by cariboo on 2011-11-26
Instead of just posting speculations, why don't you tell us what makes you think your system has been compromised.

---

### Post by Dangertux on 2011-11-27
> **MegaTopx said:**
> Is  sudo netstat -anltp|grep :80 the only way to check for backdoors? Could anything be hidden?

My results were:

tcp        0      0 [MY_IP]:46606      74.125.225.40:80        ESTABLISHED 1616/firefox-bin
tcp        0      0 [MY_IP]:46224      74.125.225.51:80        ESTABLISHED 1616/firefox-bin
tcp        1      0 [MY_IP]:38450      91.189.89.31:80         CLOSE_WAIT  2388/gvfsd-http 
tcp        0      0 [MY_IP]:40579      74.125.225.60:80        ESTABLISHED 1616/firefox-bin

and I did again right after, my results were:

tcp        1      0 [MY_IP]:38450      91.189.89.31:80         CLOSE_WAIT  2388/gvfsd-http 
tcp        0      0 [MY_IP]:40579      74.125.225.60:80        ESTABLISHED 1616/firefox-bin

And how would I configure a router or firewall? Would it be too late if there was already an intruder?

Okay first things first. I agree completely with what cariboo907 said. Is there a reason that you think you're compromised? A healthy sense of paranoia is okay, but an overwhelming fear that you've been compromised without justification is just unhealthy.

Now to address some of the issues you're having. First that command you used is only going to show you connections related to port 80, which is commonly associated with web traffic. 

a more appropriate command would be doing the following

```

sudo netstat -nlp

```Preferably without a browser or any other internet connected applications running, this helps cut down unnecessary traffic.

If you'd like you can post those results here.

To answer another question you had, yes ports and process can be hidden. If you use an application like rkhunter, it can show hidden processes and ports.

```

sudo apt-get install rkhunter
sudo rkhunter --check

```(note it WILL give you a couple of warnings about hidden files, this is because of how Ubuntu does things, this does NOT mean you are owned.)

If you'd like to post more details about why you think you're compromised we can probably help better. Otherwise here are some resources.



Ubuntu Security Sticky : [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)
How to create a firewall with Ubuntu : [http://ubuntuforums.org/showthread.php?t=1876124](http://ubuntuforums.org/showthread.php?t=1876124)

What a backdoored system actually looks like, and how a firewall helps and doesn't help  :  [http://dangertux.wordpress.com/2011/10/03/a-firewall-is-not-a-catch-all/](http://dangertux.wordpress.com/2011/10/03/a-firewall-is-not-a-catch-all/)

Security Guide For "newbies" : [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

Hope this helps.

P.S : There is no such thing as open ports you're not using.

---

### Post by Thewhistlingwind on 2011-11-27
You could always nmap scan yourself.

nmap [your ip]

---

### Post by Dangertux on 2011-11-27
> **Thewhistlingwind said:**
> You could always nmap scan yourself.

nmap [your ip]

Please note -- since you're probably paranoid, if you do this , you will probably see port 631 open, you're not backdoored it's cups lol.

---

