---
title: "Using desktop firewall to seperate wireless clients"
date: 2010-11-11
forum: Security
---

### Post by dogdo on 2010-11-11
Basically I have a wireless router with 2 pc's-one with windows xp and another with ubuntu 10.04. I want the ubuntu pc to connect to the wireless ok but i want the ubuntu firewall to block any incoming or outgoing traffic from/to the windows pc (both windows pc and ubuntu pc will share the same lan on the wireless network at the same time). Ideally id like to be able to do this with gufw interface, im not the great with ip tables in terminal.

Thanks

---

### Post by dogdo on 2010-11-12
Bump Bump

---

### Post by dogdo on 2010-11-12
> **dogdo said:**
> Basically I have a wireless router with 2 pc's-one with windows xp and another with ubuntu 10.04. I want the ubuntu pc to connect to the wireless ok but i want the ubuntu firewall to block any incoming or outgoing traffic from/to the windows pc (both windows pc and ubuntu pc will share the same lan on the wireless network at the same time). Ideally id like to be able to do this with gufw interface, im not the great with ip tables in terminal.

Thanks

I just realized-i have the ip tables firewall via gufw to deny all incoming connections and allow all outgoing connections. So would that mean in order for the windows pc to get access to my linux box i would have to explicitly open up some port/service for the windows pc to connect to me? I dont have any open ports/services so if the windows pc is infected by something and tries to connect to the linux box should the ip tables firewall block it? (bearing in mind both the widows pc and linux box will be on the same wireless local area network).

---

### Post by cariboo on 2010-11-12
If you have all incoming ports blocked on your Ubuntu computer, nothing can connect. If you wanted to share files between the two system, you would have to install samba, then unblock ports  139 + 445.

If your router has a builtin firewall, most of this is moot, as you are already running a firewall, so you don't really need a second one.

---

### Post by dogdo on 2010-11-12
> **cariboo907 said:**
> If you have all incoming ports blocked on your Ubuntu computer, nothing can connect. If you wanted to share files between the two system, you would have to install samba, then unblock ports  139 + 445.

If your router has a builtin firewall, most of this is moot, as you are already running a firewall, so you don't really need a second one.

Yes i have the ip tables firewall via gufw to deny all incoming connections. Since a windows pc can easily be taken over by malware and or a major botnet i dont think maccaffe firewall would be effective in blocking malicious outbound traffic coming from that windows pc. 

Yes the netgear wireless router im using does have the hardware firewall enabled with a deny all incoming rule in place. But since the windows pc and linux box are on the same wireless lan wouldn't the hardware firewall be useless in filtering traffic between these 2 machines? thats why i want to make sure the client based firewall on ubuntu is working!

---

### Post by cariboo on 2010-11-12
> **dogdo said:**
> Yes i have the ip tables firewall via gufw to deny all incoming connections. Since a windows pc can easily be taken over by malware and or a major botnet i dont think maccaffe firewall would be effective in blocking malicious outbound traffic coming from that windows pc. 

Yes the netgear wireless router im using does have the hardware firewall enabled with a deny all incoming rule in place. But since the windows pc and linux box are on the same wireless lan wouldn't the hardware firewall be useless in filtering traffic between these 2 machines? thats why i want to make sure the client based firewall on ubuntu is working!


Yes it would, but any windows malware won't have an affect on any system running a Linux variant.

I would suggest to stop being passive about Windows malware, be aware of where you are going on the internet, Think before you click that link goes a long way to help stay malware free.

---

### Post by dogdo on 2010-11-13
So just to reintegrate having the gufw firewall to deny all incoming and having no open ports/services should protect my ubuntu box from being attacked by someone else on the same wireless local area network?

Well i do all the basics in relation to local security-install updates, firewall, run as a low level user (sudo), apparmor is enabled, and i use a ton of firefox addons like noscript. And other obvious stuff too like decent passwords, encryption on all external drives and in home folder too. 

Arguably in relation to a virus attacking ubuntu the user would have to be fooled somewhat into installing something stupid or doing something stupid like enabling ssh with a weak password or running as root all the time right?

---

### Post by CharlesA on 2010-11-13
Correct. You'll be fine.

As for Windows being compromised, that only happens if you are stupid with yer browsing/downloading habits or are click happy at anything that prompts you to install something.

---

