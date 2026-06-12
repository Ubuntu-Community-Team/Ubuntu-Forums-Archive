---
title: "Hello...New Here"
date: 2009-06-06
forum: The Cafe
---

### Post by onetheme on 2009-06-06
It's me zeeshi from PK.
 New to this forum and would love to know more about games.

---

### Post by Barrucadu on 2009-06-06
It's who from where?

---

### Post by dragos240 on 2009-06-06
Nowhere land!

---

### Post by Bölvaður on 2009-06-06
Hi. We dont have many other people here from Pakistan (perhaps they are faking to be indian).

Games are often played to test ones wits against another's where both players get equal chance to win and take turns moving pieces/units.

*added*
about games: check the game subforum on these forums

but here is a short list of my favorite:
warsow, nexiuz, spring, crack attack, teeworlds, xmoto, penumbra, wormux.

quake live in few days.
world craft (if you work for blizzard.. other's do not get the linux version)

---

### Post by benny bronx on 2009-06-06
> It's who from where?

zeeshi from PK, pay attention (PK?)

> New to this forum and would love to know more about games.


There are many cool games native to linux.  Unfortunately, I am not much of a gamer so you will have to wait for a better reply. but I love OpenArena ( Oh, you shot kyonshi, "oooooh")

---

### Post by |{urse on 2009-06-06
do you mean coding games?

---

### Post by pwnst*r on 2009-06-06
wow, lots of bots/spam today.

---

### Post by benny bronx on 2009-06-06
> We dont have many other people here from Pakistan (perhaps they are faking to be indian).

+5 for a Pakistani presence in this formum.  In my limited experience, good people and good neighbors. Urdu is tough to learn however.  Will give it a shot after I tackle English.

---

### Post by robertguy624 on 2009-06-06
Hi Everyone,

As my message title suggests I'm totally new to  Unbuntu (version 9.04)

On buying a new PC I decided it was the perfect time to move over to Ubuntu and kick Windows into touch once and for all.

I'm pleased to report that the process has been relatively painless - and I'm getting on rather well with my new Ubuntu OS!

I have however encountered a problem when trying to install Java, and I'm hoping someone out there might be able to lend a helping hand.

I've tried to install using every method I can think of (Add/Remove, Terminal and also directly via the Java website)

However I encounter the same error message: 

'E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.'

If anyone knows what this message means and what I need to do to install Java I'd appreciate your help.

Many Thanks

Bobby

---

### Post by Daveski on 2009-06-06
dpkg is the package manager and looks after the database of installed packages and their dependants. The message is telling you that something has gone wrong and will need this command:

```
sudo dpkg --configure -a
```

run from the terminal to fix it. This command means:

> --configure package...|-a|--pending
              Reconfigure an unpacked package. If -a  or  --pending  is  given
              instead  of  package, all unpacked but unconfigured packages are
              configured.

What it should do is reconfigure any packages that were decompressed but not fully configured. Once this is sorted, try Synaptic Package Manager from the System, Administration menu and search for Sun Java JRE.

---

### Post by robertguy624 on 2009-06-06
Hi Daveski,

Thanks so much for the quick response :-)

After entering 'sudo dpkg --configure -a' , I now get the message ' [sudo] password for (username), however it wont let me enter any text....am I going mad or am I missing something?

Sorry to be a pain!

Bobby

---

### Post by Daveski on 2009-06-06
No that is fine. The command starts with sudo which tells Ubuntu to run the command with administrator (root) rights. It needs you to type in your password (the normal one you use to log in) BUT it will not show any signs that you are typing. Type the password and hit return.

---

### Post by robertguy624 on 2009-06-06
Thanks once again, Java now installed!

---

