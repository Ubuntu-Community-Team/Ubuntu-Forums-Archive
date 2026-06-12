---
title: "Automatic log in, automatic screen lock"
date: 2022-02-01
forum: Security
---

### Post by bs892 on 2022-02-01
I would like Ubuntu to automatically log in and automatically lock the screen upon startup. It would be quicker to access the computer once everything has booted, then enter a password to unlock the screen for use. This is a 1st world problem, yes.

---

### Post by DuckHook on 2022-02-01
An interesting concept: you don't want to bypass challenge/response (which is a good thing), you just want to delay it.

Conceptually, one could turn on automatic login (an easy switch in your GUI settings) and have a script that simply activates screen lock tied to "Startup Applications".

One of the problems I see with this approach is that you won't be decrypting your keyring. Automatic login has the effect of bypassing keyring activation. That means that you will have to enter your password again for anything that requires the keyring. All&#8209;in&#8209;all, that's more trouble than this workaround is worth IMO.

I'm struggling to understand the need. When my systems boot, the login process doesn't start until most of the time-consuming stuff is already out of the way. The wait is before the login screen, not afterwards. This means that the system already works the way you want, so why is this workaround even necessary?

---

### Post by bs892 on 2022-02-01
The computer I use in my shop takes a while to finish booting after log in. I plan to get a SSD one day.

It boots up, auto loads Firefox and Spotify, both of which take a while to load. By a while, I mean like 15-20 seconds. It's not that big a deal but it would be nice if it logged in, and then locked the screen. That way the power button can be pressed and 2-3 minutes onward it's instantly ready after the password entry.

---

### Post by DuckHook on 2022-02-01
> **bs892 said:**
> The computer I use in my shop takes a while to finish booting after log in. I plan to get a SSD one day.

It boots up, auto loads Firefox and Spotify, both of which take a while to load. By a while, I mean like 15-20 seconds. It's not that big a deal but it would be nice if it logged in, and then locked the screen. That way the power button can be pressed and 2-3 minutes onward it's instantly ready after the password entry.
15 to 20 seconds to load FF and Spotify is unusual. Is it an older computer? The procedure I outlined should achieve your goal, but it still seems awfully Rube&#8209;Goldbergish to me. And, among other things, the idea of autologin gives me the willies. It means that you've basically nerfed Linux's security model. And if the computer is in your shop, then depending on how exposed this machine is to the public, that is definitely ***Not*** A Good Thing.

I'm wondering it there isn't a better way to approach this:

If you don't need FF and Spotify immediately up and running (and why would you) then consider the following: Allow the system to boot up naturally and login properly with the whole challenge/response thing. Then script FF and Spotify to autostart but with a 60 second or 120 second pause. This way, they won't delay your login process, but will load after it.

---

### Post by bs892 on 2022-02-01
If it auto logs in, and locks the screen, then needs a password to unlock the screen, that's fine with me as well as what I'm looking for. Thank you otherwise

---

