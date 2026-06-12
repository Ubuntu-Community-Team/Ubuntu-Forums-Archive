---
title: "Unlock specific passwords (e.g. Ubuntu One) from keyring automatically (but not all)?"
date: 2010-04-06
forum: Ubuntu One (CLOSED)
---

### Post by merry_meerkat on 2010-04-06
I have set my computer to auto-login and as a result, the keyring asks me to enter my password every time I start the computer in order to access the password for the Ubuntu One client.

The whole point of auto-login was to not have to enter a password.

Is there a **sensible** way to use Ubuntu One without having to supply a password each time?

I say sensible, because I would like to avoid leaving the keyring totally open. I understand the purpose of the keyring, and that it should be locked by default. As far as I can see, the only potential work-arounds for the problem I am having seems to be to set the keyring password blank, thereby exposing all my keys to anyone on the computer. This option obviously defeats the purpose of having a keyring in the first place.

Is there not an option that lets me set that **specific passwords** are available automatically to **specific applications**? So that the entire keyring remains locked, but those passwords I deem ok to be unsecured are available to those applications I deem trustworthy? This option seem to exist for network-manager, why not for the Ubuntu One client?

Is this option not available, or am I missing something? If it isn't, I guess that I'll stop using Ubuntu One, which would be a shame.

Many thanks!

---

### Post by joshuahoover on 2010-04-06
> **merry_meerkat said:**
> I have set my computer to auto-login and as a result, the keyring asks me to enter my password every time I start the computer in order to access the password for the Ubuntu One client.

The whole point of auto-login was to not have to enter a password.

Is there a **sensible** way to use Ubuntu One without having to supply a password each time?

I say sensible, because I would like to avoid leaving the keyring totally open. I understand the purpose of the keyring, and that it should be locked by default. As far as I can see, the only potential work-arounds for the problem I am having seems to be to set the keyring password blank, thereby exposing all my keys to anyone on the computer. This option obviously defeats the purpose of having a keyring in the first place.

Is there not an option that lets me set that **specific passwords** are available automatically to **specific applications**? So that the entire keyring remains locked, but those passwords I deem ok to be unsecured are available to those applications I deem trustworthy? This option seem to exist for network-manager, why not for the Ubuntu One client?

Is this option not available, or am I missing something? If it isn't, I guess that I'll stop using Ubuntu One, which would be a shame.

Many thanks!

There is currently no way to set specific passwords for specific applications when it comes to the keyring. Ubuntu One is only one of a number of applications that make use of the keyring so this is going to be an issue for those applications as well. The best option is to have an Ubuntu login so that you only login once - period. As you pointed out, the other options are either annoying (having auto-login but getting prompted for a keyring password) or not very secure (setting a blank keyring password which leaves passwords in open text on your computer).

Thank you,

Joshua

---

### Post by merry_meerkat on 2010-04-06
That's a pity. I guess that I'll use dropbox then.

Just a thought: perhaps the developers of Ubuntu One should consider giving the user the option to store the Ubuntu One password unsecure within the application (with suitable warnings about the lack of security, if chosen). It's a bit of a turn-off for users who have decided that the door to their house is enough security.

And here's a question: the usual answer to this query seems to be: "don't do auto-login and your problem goes away." Does this mean that if I do have a login, that once I log in my keyring gets unlocked (just like with the blank password)?

Thanks!

---

### Post by joshuahoover on 2010-04-07
> **merry_meerkat said:**
> 
And here's a question: the usual answer to this query seems to be: "don't do auto-login and your problem goes away." Does this mean that if I do have a login, that once I log in my keyring gets unlocked (just like with the blank password)?


If you have an Ubuntu login set, then the keyring password gets automatically unlocked if the keyring password and Ubuntu password are the same. 

Thank you,

Joshua

---

### Post by AP0ll0UK on 2010-04-08
> **joshuahoover said:**
> If you have an Ubuntu login set, then the keyring password gets automatically unlocked if the keyring password and Ubuntu password are the same.

Hi Joshua

I have the same password set for both yet I am being presented with the 'unlock' message.

Is this indeed a bug within Lucid or is it by design?

Thanks.

---

### Post by Paddy Landau on 2010-04-08
I haven't used Lucid (and therefore I haven't used Ubuntu One), but I do know of a way to suppress passwords for specific programs. I am presuming -- and I may be wrong -- that it's your login password it asks for.

Here are the instructions. Note that every command is case-sensitive.

[LIST=1]
[*]Find the path to the program; in this case, Ubuntu One. As I say, I haven't used Lucid, so I guess the path would be something like [FONT=Courier New]/usr/bin/ubuntuone[/FONT]. You need to find out.
[*]Edit the sudo file. You must *not* use a normal editor; the command to use (from the terminal) is```
sudo visudo
```You will be presented with a *vi* editor. If at any time you make a mistake, press the following 5 keys, one at a time, in this order, to abort: [FONT=Courier New][SIZE=3][COLOR=Sienna]Esc : q ! Enter[/COLOR][/SIZE][/FONT] (yes, I know, it looks a bit strange!), then you can try again.
[*]Use your down-arrow to scroll to the end of the file.
[*]Create a new line by pressing [FONT=Courier New][SIZE=3][COLOR=Sienna]o[/COLOR][/SIZE][/FONT] (that's the lowercase letter O).
[*]Now type the following, exactly as specified, replacing *name* with your login name and *path* with the path from step 1:```
*name* ALL = NOPASSWD: *path*
```For example,```
merrymeerkat ALL = NOPASSWD: /usr/bin/ubuntuone
```(The path is probably wrong.)
[*]Double-check that everything looks correct.
[*]To save your changes, press the following 4 keys, one at a time, in this order: [FONT=Courier New][SIZE=3][COLOR=Sienna]Esc : x Enter[/COLOR][/SIZE][/FONT]
[*]Then type the following at the terminal (or just reboot).```
sudo -K
```
[/LIST]
I hope that works for you.

---

### Post by Paddy Landau on 2010-04-08
Hmm, I notice a couple of things.

One: There's a way to use gedit instead of vi as your editor. For the command in step 2, type```
sudo VISUAL=/usr/bin/gedit visudo
```Two: I see that the syntax of the added line is not entirely correct (yet it works for me!). It should read as follows:
```
*name* ALL=(ALL) NOPASSWD: *path*
```

---

### Post by joshuahoover on 2010-04-08
> **AP0ll0UK said:**
> Hi Joshua

I have the same password set for both yet I am being presented with the 'unlock' message.

Is this indeed a bug within Lucid or is it by design?

Thanks.

Normally there is an option from the keyring password prompt to "Automatically unlock this keyring when I log in." I'm attaching a screen shot in case that helps. This will normally pop up the first time you unlock the keyring.

Thank you,

Joshua

---

### Post by serpetiello on 2010-10-17
> **joshuahoover said:**
> Normally there is an option from the keyring password prompt to "Automatically unlock this keyring when I log in." I'm attaching a screen shot in case that helps. This will normally pop up the first time you unlock the keyring.

Thank you,

Joshua

That *"Automatically unlock this keyring when I log in."* prompt does not appear on the keyring password dialog after booting / logging in Ubuntu 10.10 :(

I have a tablet PC (keyboardless) and it's quite annoying to answer to passwords dialogs from time to time.

---

### Post by nina.melnichuk on 2011-08-09
You can set the keyring password to blank.

Go to System/Preferences/Password and Encryption keys, right click the appropriate folder and click Change Password. Put in your old password and leave the new one blank.

---

