---
title: "Can this be legal?"
date: 2006-11-27
forum: The Cafe
---

### Post by finferflu on 2006-11-27
I've received this link in my messenger, I was curious and followed it, and was kind of amazed, what do you think? can this all be possibly legal? It looks like breach of privacy to me. Is there anything that can be done about it?

I put the link at the end of the post, because I don't want to be mistaken for a spammer, I just want to know your opinion about it:

[http://darksoulmedia.com/?](http://darksoulmedia.com/?)

---

### Post by xopher on 2006-11-27
Doesn't look that legit actually. I know I wouldn't want anyone peeping in on my diskussions. This is probably why I've disabled logging -- oh, and this is a windoze app? ;)

And because of that, I'd run a dozen virus scans on it before trying it out, if that's what you intend to do..

---

### Post by shin on 2006-11-27
Well. This kind of software is legal. It does nothing without user's knowledge and it is up to user how will it be used.
Of course, one may use it to breach sb's privacy. But I don't think software creator may be held responsible for that.

---

### Post by finferflu on 2006-11-27
> **shin said:**
> Well. This kind of software is legal. It does nothing without user's knowledge and it is up to user how will it be used.
Of course, one may use it to breach sb's privacy. But I don't think software creator may be held responsible for that.

Well, the question "*Want to read the conversations your husband, wife and kids are having on Yahoo Instant Messenger and MSN while using your computer?*" sounds like and invitation to breach somebody's privacy...

---

### Post by finferflu on 2006-11-27
> **xopher said:**
> Doesn't look that legit actually. I know I wouldn't want anyone peeping in on my diskussions. This is probably why I've disabled logging -- oh, and this is a windoze app? ;)

And because of that, I'd run a dozen virus scans on it before trying it out, if that's what you intend to do..

Ah by the way, I **do not** intend to have *anything* to do with that kind of lame software... I was just intending to report it to some kind of authorities if it's illegal... And by the way, I have deleted Windows for good! ;)

---

### Post by Johnsie on 2006-11-27
Legal? Yes if it's your computer, no if it's not. In some countries or situations you may have to inform the user that their convo is being recorded. Is it Moral? That's debatable. Most people would say it's immoral but I suspect there are a few people who would disagree for various reasons.

---

### Post by jdong on 2006-11-27
If you're using it on a private computer at home that you preferably own, then most likely yes, it is legal.

But at least in the US there are legal consequences if you use it on a computer that you don't own, don't inform users that you are spying on them, or use it to retrieve passwords that you then use to hack (err, well, I guess access) into other systems.

I think this is a great security wakeup call to the anyone who thinks their stored passwords are safe...

---

### Post by finferflu on 2006-11-27
> **jdong said:**
> 
I think this is a great security wakeup call to the anyone who thinks their stored passwords are safe...

I still hope Linux is immune to that kind of softwares...

---

### Post by darkninja on 2006-11-27
"MSN & Yahoo Message Archive Viewer decodes the archives stored in your computer. Works even if you don't have the login password."

Aren't MSN and Yahoo logs stored in plaintext? Either way, disable logging to defeat this program.

---

### Post by jdong on 2006-11-27
> **finferflu said:**
> I still hope Linux is immune to that kind of softwares...

Well, not entirely. It all depends on how your store that kind of data.

If it's passwords, most places that Ubuntu allows you to save passwords, encrypts them. This includes almost every GNOME application (the GNOME keyring), Firefox if you set a Master Password. Unfortunately, notable applications that it doesn't include include the GAIM instant messenger.

Also, GAIM logs are stored in plaintext.

At any rate, you can protect yourself by:

(1) Making your home folder private if you share the system with other people. You can do this by removing world read, write, and execute permissions with a command like **chmod o-rwx ~/**.

This will not allow any user but you (and those in your private group.. by default no one) to access your home directory. Everyone else gets Permission Denied.

(2) Insisting adamantly that others do not share your account. Don't let other people use your login name. Give them their own.

(3) Hand out sudo access considerately. Remember that sudo users are not affected by these permissions and have full control over every aspect of the system.

(4) Obvious, but often missed: Don't store sensitive data! Decide if it's worth the convenience. Be aware if your program stores passwords in an encrypted keyring or in plaintext.



These are really simple ways to protect yourself that requires almost no sacrifices on your part.

However, they only offer a surface level of protection. This protection can all be bypassed via a LiveCD or taking out the hard drive and putting it into another machine.

More robust security measures include:

(1) Set a BIOS bootup password and a GRUB bootloader password (check /boot/grub/menu.lst for details on how to do that). Actually, this is pretty flimsy too, but at least provides another barrier to casual tamperers.

(2) Encrypt your home directory. This takes much more work and technical knowledge but there are excellent guides on dm-crypt and how to encrypt /home with cryptsetup. If you really think your system is under enough of a threat to warrant this, then you may want to take some time in encrypting your /home.

---

### Post by jdong on 2006-11-27
> **darkninja said:**
> "MSN & Yahoo Message Archive Viewer decodes the archives stored in your computer. Works even if you don't have the login password."

Aren't MSN and Yahoo logs stored in plaintext? Either way, disable logging to defeat this program.

Yeah, those programs aren't anything more than an overglorified notepad with a few built-in paths to look in.

---

### Post by Frak on 2006-11-27
If you own it, I mean the computer, then you can do whatever you want with it as long as it doesn't cause damage to any other property, that's not yours.

---

### Post by finferflu on 2006-11-28
> **Frak said:**
> If you own it, I mean the computer, then you can do whatever you want with it as long as it doesn't cause damage to any other property, that's not yours.

If I own a computer and let other people use it for their private business, I don't think I'm entitled to look into that... I don't own people's privacy.

---

### Post by Tomosaur on 2006-11-28
The logs aren't even encrypted. Last time I checked, MSN stored its logs in some weird XML format, but they could still be read using any text editor and a little patience. All this seems to do is apply formatting to the XML to make the logs look nice.

Maybe in the later versions of MSN the logs are encrypted, but when I last looked, they weren't, and were open for all to read if they really wanted to.

---

### Post by jdong on 2006-11-28
> **Tomosaur said:**
> The logs aren't even encrypted. Last time I checked, MSN stored its logs in some weird XML format, but they could still be read using any text editor and a little patience. All this seems to do is apply formatting to the XML to make the logs look nice.

Maybe in the later versions of MSN the logs are encrypted, but when I last looked, they weren't, and were open for all to read if they really wanted to.
they still aren't. Most of these programs just look around the disk or the registry for plain-text passwords and present them to the user in a list. None of it is information that Windows Explorer and regedit wouldn't be able to get for a knowledgeable user.

---

