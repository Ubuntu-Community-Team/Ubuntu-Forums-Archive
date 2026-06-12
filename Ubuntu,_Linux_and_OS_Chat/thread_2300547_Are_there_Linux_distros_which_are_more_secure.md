---
title: "Are there Linux distros which are more secure?"
date: 2015-10-26
forum: Ubuntu, Linux and OS Chat
---

### Post by remmas-sido on 2015-10-26
Hello guys 
Can you say Fedora is more secure than Ubuntu, Ubuntu is less secure than Slackware and so on... I mean are all Linux distros equals in security?

---

### Post by Habitual on 2015-10-26
Any OS is only as secure as the nut behind the keyboard.

---

### Post by monkeybrain20122 on 2015-10-26
It is how you configure it really. Fedora is 'more secure' because by default Selinux blocks almost everything. It is such a pain that normal desktop users would probably want more  permissive configurations. Conversely, if you are really paranoid you can configure appamour in Ubuntu to be more restrictive.

---

### Post by lisati on 2015-10-26
Sometimes it boils down to not so much a question of more or less, but just different.

---

### Post by night_sky2 on 2015-10-26
Ubuntu is based on Debian's architecture and infrastructure so it's foundation is rock-solid. That being said, Ubuntu developpers are commited to the OS and quickly provides security updates when needed.
But I guess it all depends on your particular definition of ''security''. For standard computer usage, Ubuntu meets the security needs ot it's users. That is what is relevant to me.

---

### Post by grahammechanical on 2015-10-26
Also, by what you mean with the word "secure."

In comparison with distributions that create a root account Ubuntu is more secure because the root account is locked in Ubuntu. 
> 
There are a number of benefits to Ubuntu leaving **root** logins disabled by default, including: 


[LIST]
[*]The installer has fewer questions to ask. 
[*]Users  don't have to remember an extra password for occasional use (i.e. the  root password).  If they did, they'd be likely to forget it (or record  it unsafely, allowing anyone to easily crack into their system). 
[*]It avoids the "I can do *anything*"  interactive login by default.  You will be prompted for a password  before major changes can happen, which should make you think about the  consequences of what you are doing. 
[*]sudo adds a log entry of the command(s) run (in /var/log/auth.log). If you mess up, you can go back and see what commands were run. 
[*]On a server, every cracker trying to *brute-force* their way in will know it has an account named **root**  and will try that first. What they don't know is what the usernames of  your other users are. Since the root account password is locked, this  attack becomes essentially meaningless, since there is no password to  crack or guess in the first place. 
[*]Allows  easy transfer for admin rights by adding and removing users from  groups.  When you use a single root password, the only way to  de-authorize users is to change the root password. 
[*]sudo can be setup with a much more fine-grained security policy. 
[*]The  root account password does not need to be shared with everybody who  needs to perform some type of administrative task(s) on the system (see  the previous bullet). 
[*]The  authentication automatically expires after a short time (which can be  set to as little as desired or 0); so if you walk away from the terminal  after running commands as root using sudo, you will not be leaving a  root terminal open indefinitely. 
[/LIST]


Like other distributions Ubuntu is still using the xserver. So, Ubuntu is neither more secure or less secure. The latest versions of Ubuntu use the latest Linux kernels. So, Ubuntu is as secure as any distribution using the latest Linux kernels.

Like other Linux distributions users are not prevented from downloading software from web sites and then installing it and so opening the system to the possibility of running malicious code. Like other distributions Ubuntu uses open source software from other projects, such as Debian and Gnome, and the Ubuntu developers can therefore audit the source code. In this way Ubuntu is not less secure than other distributions that make use of software from Debian, Gnome, the GNU project (Grub), RedHat (systemd), and others.

Regards.

---

### Post by mastablasta on 2015-10-27
there are distros that would use Tor by default, wipe out RAM on exit, use hardened kernel etc., etc. so yes there are those that have more secure options but may be a bit more annoying to use for normal user. we are talking about default settings here. ofcourse nothing prevents you to modify Ubuntu for example to also have all that stuff enabled - for more see: [https://help.ubuntu.com/community/Security](https://help.ubuntu.com/community/Security)

---

### Post by buzzingrobot on 2015-10-27
> **remmas-sido said:**
> ... I mean are all Linux distros equals in security?

For home and personal use, I think any of the major distributions supported by large communities and/or corporations deliver equivalent security. They all have access to the same patches from the same sources and they all have track records of packaging those sources and pushing them out quickly.

User behavior is the biggest factor in user security.  The quickest updates possible will not protect you from your own bad behavior. Don't imagine any distribution will magically keep you safe while you click anywhere and everywhere.

Tools like SELinux, etc., target institutional and corporate users and are typically poorly explained to individual users who often just turn them off rather than be annoyed, thereby eliminating the protection they do provide. (Since it's a pet peeve of mine, I put KDE's KWallet in that category, a well: Poorly presented and explained to users, and so annoying in operation that people just disable it.)

---

