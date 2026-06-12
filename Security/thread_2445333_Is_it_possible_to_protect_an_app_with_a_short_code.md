---
title: "Is it possible to protect an app with a short code, e.g. a PIN?"
date: 2020-06-12
forum: Security
---

### Post by Paddy Landau on 2020-06-12
Is it possible to protect an app with a short code, e.g. a PIN, so that it won't open until the code is entered?

I have a password manager ([KeepassXC]("https://keepassxc.org/")) that, once unlocked, sits in my taskbar. To reopen it, all that a person has to do is click on the icon. That's insecure. Locking it every time after I use it makes me enter a long passphrase to reopen it, which quickly becomes unwieldy.

I'd like to protect KeepassXC with a short code (not necessarily digits), so that once unlocked, clicking the icon will open the KeepassXC window only after the short code has been entered. It would be extra useful if entering an incorrect code (say) three times would force-close KeepassXC to prevent brute-force guessing.

This functionality would replicate the "Quick Unlock" function provided by [KeePass2]("https://keepass.info/") + [Quick Unlock]("https://keepass.info/plugins.html#quickunlock"), or by [Keepass2Android]("https://play.google.com/store/apps/details?id=keepass2android.keepass2android").

I've spent some time searching for solutions, but finding nothing apart from the fact that using [PAM for a lockscreen PIN]("https://unix.stackexchange.com/a/147355/41226") is possible.However, I don't know PAM, so I don't know if it can be applied to opening a window whose program is already running in the background.

Do you have an idea of how to implement this, whether using PAM or some other way?

---

### Post by EuclideanCoffee on 2020-06-12
PAM would be your way of authenticating with a pin.

The problem then is that modifying PAM may allow you to authenticate anything with a pin.

I use PAM only sparingly and do not create pins with it. I'm sure there may already be a good way to do this, but it's not obvious at first to me what you'd need to do. This would require some digging, which anyone could do.

If you place a pin wrapper around any application launcher script, you are only using security theater because anyone could bypass the launcher with a direct path to the application from your computer. If you modify the /usr/bin, someone could still figure out the path and bypass your /usr/bin path. Plenty of people may already give you this advice. I think it only gives you a sense that there is improved security, when in reality it's just wasting your time.

Therefore your real option appears to place sudo restrictions on the binary. But you said you have too long of a password, and giving the application a sudo path would only allow it possible root access to your computer. Not good.

These are the things you can do.

But what are things you cannot immediately do that would have a direct impact on your security?

You can rewrite the application to ask for a pin upon startup. That pin answer is encrypted, so the user won't have direct access to it. And they would have to enter the pin number manual to bypass security.

But this obviously isn't secure either. All an attacker would need to do is break the function that asks you for a password. As soon as they can figure this out, they can likely get direct access quite easily.

All of this then depends on where you are, what you are protecting, and who you are protecting it from.

If you are protecting data from a non-technical user, you may want to hide the document as a dot file.

If you are protecting data from a technical user, you may want to put the data in Dropbox or OneDrive where it's behind someone else's security system.

Etc.

---

### Post by TheFu on 2020-06-12
Just brainstorming here ... 

You could create a new userid that can only run the specific command and lock down that userid so no direct logins are allowed.
Then you can modify some sudo settings to let your userid, and only yours, run the command as that other userid leveraging sudo for authentication.

Or you could just have a portable version of the program, store it inside an encrypted container that you'd unlock, mount with 700 permissions, and unmount when done. Heck, with 700 permissions and a portable application, that might be sufficient.

As EuclideanCoffee suggests, the sort of attacker would matter greatly. Are you trying to protect against the NSA, Chinese, Russian, Turkish, or Israeli Security teams or against an 8 yr old grand child?  Someone with sufficient technical knowledge can access everything on a non-encrypted disk and may be able to trick you into providing access even if it is encrypted by modifying the /boot/ areas.

A pin really isn't much security, unless it is tied to a physical challenge/response device. Even then, why have just a pin? Use a passphrase for the challenge and have the device provide the response to unlock whatever it is - that could be LUKS or sudo or something else.

---

### Post by Paddy Landau on 2020-06-12
> **EuclideanCoffee said:**
> All of this then depends on where you are, what you are protecting, and who you are protecting it from.> **TheFu said:**
> As EuclideanCoffee suggests, the sort of attacker would matter greatly.
Thank you, EuclideanCoffee and TheFu. I'm not protecting any state secrets or dodgy activity here :) Just a normal password manager.

I was hoping for something quite simple, but it looks like it will be complex. I'll leave it until the KeepassXC team programs Quick Unlock (it has been promised, but as it's a free product, it might take a long time).
> **TheFu said:**
> … tied to a physical challenge/response device.
Unfortunately, the database (which, encrypted, is synchronised via Dropbox) is also used on an Android device, which does have Quick Unlock. So, alas, a physical device won't cut it.

It looks as though this is something that I'll have to live with until the programmers for KeepassXC find the time to do this work.

Thanks again for your input!

---

