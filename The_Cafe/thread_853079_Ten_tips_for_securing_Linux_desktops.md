---
title: "Ten tips for securing Linux desktops"
date: 2008-07-08
forum: The Cafe
---

### Post by sharks on 2008-07-08
[http://resources.zdnet.co.uk/articles/tutorials/0,1000002006,39442143,00.htm](http://resources.zdnet.co.uk/articles/tutorials/0,1000002006,39442143,00.htm)

---

### Post by OmniCloud on 2008-07-08
Tks man...Useful simple information...

---

### Post by gunashekar on 2008-07-08
Wish the article also listed services that can be stopped and the role of each service.

---

### Post by Greyed on 2008-07-08
The thing is that the services one would want to run are individual and outside the scope of the article.  The advice is general, "look here and think!"  The article can't do the thinking for you.

For Ubuntu and sisters that bit of advice is somewhat superfulous.  Those services are not even installed on the desktop version.  Furthermore, at least on KDE 3.5.9, those services can be configured by the DE and it does let you know what each service does.  If one is really incluned to figure out what's going on doing a google on the program name would no doubt bring up the information one needs to make an adequatee decision.

---

### Post by tamoneya on 2008-07-08
Honestly I didnt find it all that useful.  

1. Putting a "." in front of your directories and files isnt my idea of a secure system but more like a way to hide your porn.
2. a separate /home partition isnt going to add much in terms of security.  While I think it is a nice idea in case you need to reinstall it wont prevent a hacker.  
3. using a different DE wont really help since if you get hacked the hacker will probably use command line access wont use your DE anyways.

---

### Post by aysiu on 2008-07-08
This is one of the worst articles on security I have ever seen in my life. I can't believe this was actually published. > 1. Locking the screen and logging out is important While this prevents casual snooping by non-tech-savvy family members, it's not real security against anyone who has physical access to your computer and wants to do your installation serious harm.

> 2. Hiding files and folders is a quick fix Same deal here. It's actually easier in Linux for snooping family members or friends to find your hidden files than in Windows or OS X. In Windows, it's buried deep in a submenu of a menu. In OS X, you have to copy and paste a cryptic line into the terminal. In Linux (Nautilus, Konqueror, Thunar), it's only one level deep in the menu (*Show Hidden Files*).

This is hardly security. It's basically like saying security in your household is putting your jewelry under your bed instead of on top of the bed. Yes, you won't be advertising its existence, but you're certainly not preventing anyone from getting to it.

> 3. A good password is a must
Your password on a Linux PC is your golden key. If you give that password out or if you use a weak password, your golden key could become everyone's golden key. Finally a good tip in theory, but there are no specifics about what makes a password strong or weak.

> And if you're using a distribution like Ubuntu, that password will give users much more access than, say, Fedora. To that end, make sure your password is strong. There are many password generators you can use, such as Automated Password Generator. No explanation about how Ubuntu gives users more access? I'm not too sure about this. Sounds like FUD.

> 4. Installing file-sharing applications is a slippery slope
I know many Linux users are prone to file-sharing. If you want to run that risk at home, that's your call. But, when at work, you not only open yourself, or your company, up to lawsuits, you open your desktop machine up to other users who might have access to sensitive data on your work PC. So, as a rule, do not install file-sharing tools. This is a rather broad statement that appeals to paranoia instead of reason. BitTorrent comes preinstalled in Ubuntu and is a filesharing tool that does not give others access to sensitive data. I don't know how you're able to use Linux at work, but I'd love to be able to do that. Most Linux users use Linux at home and have to use something else (like Windows) at work.

> 5. Updating your machine regularly is wise
Linux isn't Windows. With Windows, you get security updates when Microsoft releases them, which could be many months away. With Linux, a security update can come minutes or hours after a security flaw is detected. While it's true you should update regularly, I don't really understand the distinction this guy's trying to make. In Linux, you also get security updates when ________ releases them. Yes, the updates do tend to come more quickly, but as a user (not programmer) I'm still reliant on Ubuntu (since I'm a Ubuntu user) to release updates.
> 6. Installing virus protection is actually useful in Linux Actually, [it's not](http://ubuntucat.wordpress.com/2008/07/03/does-ubuntu-need-antivirus/). > 7. SELinux is there for a reason
SELinux (Security-Enhanced Linux) was created by the US National Security Agency. It helps lock down access control to applications, and does so very well.

Certainly, SELinux can sometimes be a pain. In some cases, it might take a hit out of your system performance, or you might find some applications a struggle to install. However, the security comfort you gain by using SELinux (or AppArmor) far outweighs the negatives. During the Fedora installation, you get the chance to enable SELinux. I have heard good things about SELinux.

> 8. Creating /home in a separate partition is safer
The default Linux installation places your /home directory right in the root of your system. This is fine but, firstly, it is standard, so anyone gaining access to your machine knows right where your data is; and, secondly, if your machine goes down for good, your data might be gone. This makes no sense and makes me think that this Jack Wallen person has no idea what partitions are or what mounting is. If someone has access to your machine, it doesn't really matter if your data is on a separate partition or not, unless you are encrypting that partition.

> 9. Using a non-standard desktop is worth its weight in gold

Since most users have no idea how to move around in these desktops anyway, they aren't going to have the slightest idea how to get to your files. It is simple pseudo-security. Simple pseudo-security - like most of your tips, yes.

> 10. Stopping services is best
This is a desktop machine. It's not a server. So why are you running services like httpd, ftpd, and sshd? You shouldn't need them and they only pose a security risk, unless you know how to lock them down. So don't run them. Check your /etc/inetd.conf file and make sure that all unnecessary services are commented out. It is a simple but effective method. Finally a point worth making. Fortunately, Ubuntu doesn't run server software by default. You have to enable it yourself.

What a bogus article. I hope people don't really think taking these tips will make them secure.

---

### Post by sharks on 2008-07-08
i am glad that it is useful to u.

---

