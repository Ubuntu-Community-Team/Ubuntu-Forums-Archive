---
title: "Do i need security software or not ?"
date: 2011-10-16
forum: Security
---

### Post by rishi_singh on 2011-10-16
Hi ! I use ubuntu 11.1 and I have the impression that linux is "malware-resistant" from discussions with friends who have been using it for a long time.

If its so secure, then do i really need antiviruses, firewalls, virtualization and such ? BTW, i use it mainly for surfing and other basic tasks.

---

### Post by bodhi.zazen on 2011-10-16
> **rishi_singh said:**
> Hi ! I use ubuntu 11.1 and I have the impression that linux is "malware-resistant" from discussions with friends who have been using it for a long time.

If its so secure, then do i really need antiviruses, firewalls, virtualization and such ? BTW, i use it mainly for surfing and other basic tasks.

I suggest you read the security sticky it covers most of your questions.

---

### Post by Dangertux on 2011-10-17
> **bodhi.zazen said:**
> I suggest you read the security sticky it covers most of your questions.

+1 to this.

It really depends on what you're securing and from whom though. If someone is targeting you specifically they will eventually get you. For the average every day browsing no not really, unless you completely lack common sense.

At a minimum I would suggest utilizing at LEAST , ufw, apparmor, and something like noscript. Apparmor can be a pain in the butt, but at least get a decent browser profile if nothing else.

Hope that helps.

---

### Post by MonolithImmortal on 2011-10-18
Honestly, for browsing, the most you will need is noscript. I don't even do that.

But read the sticky, it will answer a lot of your questions.

---

### Post by rishi_singh on 2011-10-28
> **Dangertux said:**
> +1 to this.

It really depends on what you're securing and from whom though. If someone is targeting you specifically they will eventually get you. For the average every day browsing no not really, unless you completely lack common sense.

At a minimum I would suggest utilizing at LEAST , ufw, apparmor, and something like noscript. Apparmor can be a pain in the butt, but at least get a decent browser profile if nothing else.

Hope that helps.

already use no script. its good. i read some stuff about being careful about what you run/install if you are a "root user". Any sticky/articles on that aspect.

---

### Post by dfarrell07 on 2011-10-28
Run noscript and HTTPSEverywhere, don't fall for pishing, and you will be fine. 

As far as root, just be wary of installing programs from untrusted sources. This applies to all OSs. Also, be aware that you can break you system. Don't modify or dlt critical files (this is painfully obvious). As long as you stay in your home directory (/home/yourusername/) you will be fine. If you need to get below that, make sure you know what you are doing.

---

### Post by agillator on 2011-10-28
Linux as is seems pretty secure. The suggestions above are certainly valid. However, I am a firm believer in Murphy's Law. As I understand it, the odds are that if someone breaks into your system the design of Linux will probably limit them to what you as a user have access to, i.e. your home directory mostly. So be careful of what groups include your user and what permissions they have outside your home directory. Do you have anything on your machine you would not want to be public knowledge or you need to keep secret such as passwords? Finally, what can you delete that you could not replace or would require an unacceptable amount of effort to replace? Those things you would need to guard to some extent. A firewall would be a good idea. Regular backups are a good idea. How much further you go depends on your answers to the questions and is up to you.

---

### Post by bodhi.zazen on 2011-10-28
> **agillator said:**
> As I understand it, the odds are that if someone breaks into your system the design of Linux will probably limit them to what you as a user have access to, i.e. your home directory mostly.

Yes, but, if they have shell access you are sort of doomed, more so if the user they crack has root access, either via su or sudo.

In addition, some vulnerabilities allow root access directly.

Rather then assuming, you should read the vulnerability report

[http://www.ubuntu.com/usn](http://www.ubuntu.com/usn)

Which lists

[http://www.ubuntu.com/usn/usn-1232-3/](http://www.ubuntu.com/usn/usn-1232-3/)

[http://www.ubuntu.com/usn/usn-1232-3/](http://www.ubuntu.com/usn/usn-1232-3/)

X and kernel vulnerabilities ...

> An authorized attacker could exploit this to cause the X server to
crash, leading to a denial or service, or possibly execute arbitrary code
**with root privileges**.

> A local attacker with physical access could
insert a specially crafted USB device **and gain root privileges**.

Emphasis added by me, and there are more vulnerabilities then those two.

Sure, physical access is root access, but typically one would use encryption. Root access by attaching a usb to a running desktop / server == root access + access to encrypted data.

Honestly, I am not sure apparmor would help with either vulnerability. You would have to have an appropriate profile in place, which would be unlikely. selinux *might* but it might not. pax (grsecurity) *might* help.

This is why we advise keeping your system up to date (security patches) and using tools such as apparmor, although they have limits as well.

---

