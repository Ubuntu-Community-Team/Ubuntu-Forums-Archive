---
title: "System hacked?"
date: 2009-09-28
forum: Security
---

### Post by jasonmichel on 2009-09-28
ok earlier today i noticed when i came back to my laptop that someone was trying to hack my login...i always lock my computer when i leave..i came back and saw someone typing and trying to get in..i didn't know if i had a key stuck or something.  after a couple attempts it stopped...i logged in and didn't notice anything..then after lunch i notice a notification that says "your desktop now being controlled by etc.."  i immediately unplugged the ethernet.  Two things, how could someone hack my laptop so easy?  I thought linux was supposed to be secure..and second..how can i prevent this?  I read something about fail2ban.  What should i look for in my auth.log file? Thanks in advance

---

### Post by doas777 on 2009-09-28
ok, first, where are you/your laptop? 
second, disable remote desktop from System -> Preferences, unless it is on YOUR local network only. that is what the notification is about.

physical security is #1. there is not a single thing you can do to prevent an even moderatly skillful attacker if they have physical access to your box. 
pick it up and take it to lunch with you. Physical access is root access. that stands for any platform. yes linux is more secure in general but no system is secure if you let me get my hands on it directly.

add a bios and grub password, and disable boot from CD in the BIOS. not foolproof, but they would have to get into the laptop case to clear the BIOS password.

check for any unauthorized user accounts, or expected ones that have more rights than they did yesterday.

do you have SSH or other remote access services enabled?
i believe that fail2ban only works with network services but it MAY work for interactive logins. my question for you is though, if a malicious user locks out your user account, do you have another that you can use to unlock your primary? if not, it will be you who is banned.

---

### Post by jasonmichel on 2009-09-28
no, its at work..it wasn't a physical access it was network access. I did disable remote desktop etc..how do i disable all remote access tools?  I checked the log but not sure what to look for..i don't see any new user accounts set up.  I am attaching a copy of my log if someone can see anything?

---

### Post by rookcifer on 2009-09-28
> **jasonmichel said:**
> ok earlier today i noticed when i came back to my laptop that someone was trying to hack my login...i always lock my computer when i leave..i came back and saw someone typing and trying to get in..i didn't know if i had a key stuck or something.  after a couple attempts it stopped...i logged in and didn't notice anything..then after lunch i notice a notification that says "your desktop now being controlled by etc.."  i immediately unplugged the ethernet.  Two things, **how could someone hack my laptop so easy?  I thought linux was supposed to be secure.**.and second..how can i prevent this?  I read something about fail2ban.  What should i look for in my auth.log file? Thanks in advance


LOL.... just.. LOL

> **jasonmichel said:**
> **no, its at work..it wasn't a physical access it was network access.** I did disable remote desktop etc..how do i disable all remote access tools?  I checked the log but not sure what to look for..i don't see any new user accounts set up.  I am attaching a copy of my log if someone can see anything?

First you said that "I came back from lunch and saw someone typing trying to get in."

And now you say it was remote access.  Pardon us for being confused by your very unclear explanation in your first post. :confused:

---

### Post by jasonmichel on 2009-09-28
yeah i can see how that would be confusing...i meant i saw data being entered on the login box to unlock the screen, and when i came back from lunch, i logged in, and i got a notification about 10 minutes later saying desktop was being remotely controlled.  Why is it funny that i expected linux to be secure...I've never had a windows box hacked..am i wrong to think that linux would be secure?

---

### Post by arvevans on 2009-09-28
Do you have a friend (or enemy) on the same LAN as your laptop, who knows a bit about UNIX or Linux shell commands?  What happens if you go to a terminal screen and do a "write [friend's local IP Address]" and type in "Your Computer Has Been Invaded By Little Green Men!", followed by hitting the ENTER key?

Point I am trying to make is that you may have been the recipient of a hoax message, and not a security attack at all.
_._

---

### Post by jasonmichel on 2009-09-28
no, noone in office etc that would be able to do that or know to do that.  The fact that it was persistent tells me it was a security breech. And the user that it said was controlling looked like it was from a public FQDN

---

### Post by XCan on 2009-09-28
It sounds like you enabled remote desktop with no password. When you lock your screen, someone can thus connect to your VNC and starting to try and brute your password.

Whatever the case, if someone gained remote access to your comp, I'm quite sure it's because either lack of password or weak password.

---

### Post by greyfox1 on 2009-09-28
> **rookcifer said:**
> LOL.... just.. LOL



First you said that "I came back from lunch and saw someone typing trying to get in."

And now you say it was remote access.  Pardon us for being confused by your very unclear explanation in your first post. :confused:

Hey, here's an idea.  Why don't you stop acting like an asshat and actually contribute something useful to the dialog here?  Don't ridicule someone for his lack of understanding.  If anything it's an opportunity to educate him.

I was not confused by what he said-- he didn't mean that there was a person sitting at his laptop typing, he meant that he saw text appearing on the screen due to someone accessing it remotely and trying to log in (or at least this is what appeared to be happening).

jasonmichel - I have someplace to be, but I'll try to have a look at your auth.log later.

---

### Post by jasonmichel on 2009-09-28
Thanks!!

---

### Post by doas777 on 2009-09-28
yep, linux is more secure, but it is also free enough to let you open a massive security hole, by enabling remote desktop witout a password (or even with one frankly).

if you actually need remote access capability, use FreeNX or tunnel all VNC sessions over SSH. and install fail2ban.

---

### Post by jasonmichel on 2009-09-28
> **XCan said:**
> It sounds like you enabled remote desktop with no password. When you lock your screen, someone can thus connect to your VNC and starting to try and brute your password.

Whatever the case, if someone gained remote access to your comp, I'm quite sure it's because either lack of password or weak password.

yeah i immediately turned off remote desktop..not sure how it got turned off..So what else should i do to secure remote access.  I looked at the ssh_config. But didn't see anything to disable log in as root.  Is it someplace else?

---

### Post by jasonmichel on 2009-09-28
> **doas777 said:**
> yep, linux is more secure, but it is also free enough to let you open a massive security hole, by enabling remote desktop witout a password (or even with one frankly).

if you actually need remote access capability, use FreeNX or tunnel all VNC sessions over SSH. and install fail2ban.

yeah, i just posted..not sure why Remote desktop was enabled...huge oversight on my part...so i have it disabled now..anything else i should do..i Don't need remote access to this workstation so I just as soon make sure there aren't any holes

---

### Post by doas777 on 2009-09-28
> **jasonmichel said:**
> yeah i immediately turned off remote desktop..not sure how it got turned off..So what else should i do to secure remote access.  I looked at the ssh_config. But didn't see anything to disable log in as root.  Is it someplace else?

check in sshd_config instead (d is for daemon => service; ssh is the client, not the server). think it's /etc/ssh/sshd_config. I always have to look for it myself.

look for a line that says "Permit Root Login" and set ti to no. also make sure you have a strong password. 14+ chars, alpha and numeric, caps and lower, and special chars (!#$%^()_=) .

---

### Post by jasonmichel on 2009-09-28
i don't see it listed in the ssh directory.. when i gedit it, its empty

---

### Post by alphaniner on 2009-09-28
> **jasonmichel said:**
> i don't see it listed in the ssh directory.. when i gedit it, its empty

Are you sure you have the ssh daemon installed?  It's not installed by default.

---

### Post by jasonmichel on 2009-09-28
i didn't install it.  so i guess i should just leave uninstalled?

---

### Post by srt4play on 2009-09-28
Install zenmap and do a scan on your laptop's ip. It will show you what services are listening for outside connections.

---

### Post by doas777 on 2009-09-28
yep. if you don;t need Remote access, then there is little point in installing it.
ubuntu in it;s default state has no network services running at all. there is no way someone can nethack you in that state, unless they obtain physical access, or manage to trick you into applying an insecure configuration.

so I think you are ready to go. just be vigilant, and you shoudl be fine.

---

### Post by jasonmichel on 2009-09-28
thanks to all who replied..understand alot more now

---

### Post by ikt on 2009-09-28
> **jasonmichel said:**
> yeah, i just posted..not sure why Remote desktop was enabled...huge oversight on my part...so i have it disabled now..anything else i should do..i Don't need remote access to this workstation so I just as soon make sure there aren't any holes

As suggested above not necessarily with nmap, just do a full port scan on your system and see what's listening for external connections.

---

### Post by doas777 on 2009-09-28
looked at your auth log, and not much stands out, other than someone installing xedit around 1:00PM.

a login failure message from the locked screen should look somthing like this:
```

Sep 28 15:25:32 computer1 unix_chkpwd[3467]: password check failed for user (<username>)
Sep 28 15:25:32 computer1 gnome-screensaver-dialog: pam_unix(gnome-screensaver:auth): authentication failure; logname= uid=1000 euid=1000 tty=:0.0 ruser= rhost=  user=<username>

```

so it doesn't look like anyone was trying to bruteforce your passwd.

---

### Post by Bölvaður on 2009-09-28
> **jasonmichel said:**
> ...someone was trying to hack my login...i always lock my computer when i leave..i came back and saw someone typing and trying to get in..i didn't know if i had a key stuck or something.  after a couple attempts it stopped...i logged in and didn't notice anything..then after lunch i notice a notification that says "your desktop now being controlled by etc.."  i immediately unplugged the ethernet.  Two things, how could someone hack my laptop so easy?

This is my guess of what happened.


Someone guessed your ip and tried to log in to VNC with an empty or a weak password and succeeded.

You saw him trying to guess user name and password (probably had the user name already filled in) but couldn't guess it (probably not a bot, and probably a low skilled hacker if so).

He might have stopped guessing to go to the toilet.

You logged in.

He came back and looked at a lovely open system to play with. Too bad he probably have never seen anything like this (as he is a low killed hacker) and wouldn't know how to cause harm on this foreign looking OS, with no idea how to gain root access.

He didn't dare to do anything to spook you off and waited until you left the computer unattended.

You locked the screen or logged off.

He probably began guessing the password again for a while before he gave up.
He probably checked everything he might be able to do and saw this "Leave a message" button. He pressed that button and typed you a nice message "Sir, all your desktop are being belong to Sir Nooby MacNoob"


VNC is not secure.

---

### Post by jasonmichel on 2009-09-28
ha, thats probably pretty close what happened..lol

---

### Post by ApEkV2 on 2009-09-28
> **Bölvaður said:**
>  "Sir, all your desktop are being belong to Sir Nooby MacNoob"

LOL......MacNoob.....lollool
awesome

---

### Post by cdenley on 2009-09-28
There are no services which allows attackers to connect remotely enabled by default which you need to worry about. If you are concerned you somehow installed servers by accident, I suggest this command.
```

sudo netstat -tlnp

```
You should see cupsd listening on 127.0.0.1:631 and avahi listening on some UDP port. Anything else would indicate a server which insn't installed by default. I would not suggest portscanners (nmap), since they can be very misleading when you scan your computer from your computer.

You don't need to worry about anything as long as you don't install packages or enable features unless you understand what they do.

---

