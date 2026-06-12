---
title: "[HOWTO]File and text encrypting with PGP"
date: 2008-08-19
forum: Security
---

### Post by Sarmacid on 2008-08-19
This is my first guide, and in it I'll show you how to encrypt files/text. I searched around and didn't find an explicit guide of how to encrypt/decrypt/share files/text so I experimented around and here's what I found out. Feel free to make any corrections and I'll try to answer any questions you have to the best of my abilities ;)

First you should know something about PGP encryption. This encryption consists of a pair of keys, wich are created at the same time, and are the private key and the public key. The public key you can share with anyone you want to have something encrypted and sent to you, the private however, you must not share with anyone, since it's the one used to decrypt. With that clear, now let's start

Firs you have to create the key pair, to do this, go to applications -> Accessories -> Passwords and encryption keys

There select from the menu Key -> Create new key...

Select PGP key and hit continue

Input the info required there(Your name, your e-mail and a comment if you want). If you click the advanced you can set up the key strength and expiration date. The higher the key strength is, the harder it will be to crack, but the more time encrypting will take. I suggest something between 1024-4096 bits, the default is good. Expiration date will be the date the key is useless, only set this if you want the key to expire.

Type your passphrase twice, remember to pick a strong passphrase(No known words, case changes, numbers, other characters)

Your key pair is now ready to use.

If you want to encrypt a file now, right click it and select encrypt.

Check the public key you want to encrypt it with, and sign it if you want. If you sign it, you will be asked for your passphrase.

To decrypt the file just open it as you would a normal file(AKA double click), enter your passphrase and there you have it.

Now, I don't like using evolution, I do all mail related stuff in gmail and I didn't want to start using evolution just to encrypt my messages, so next we'll see how to encrypt text.

Open gedit(Applications -> Accessories -> Text editor) and on the menu, go to Edit -> Preferences, click the plugin tab and check text encryption. Close preferences. Now you can type whatever you want here, then go to Edit -> Encrypt, again choose the public key you want to encrypt it with and there you should see something about PGP and a bunch of what looks like random characters. To decrypt is very easy, Edit -> Decrypt, and type your passphrase in the box. So for confidential emails just paste the mail in gedit, encrypt, paste to your mail client and you're set.(If anyone wants to add evolution or thunderbird to the guide send it to me, I'll post it and give you credit for your work)

Now, what if you want someone to send you something encrypted? Very easy, in Passwords and encryption keys go to the my personal keys tab, right click your key and select Sync and publish keys. A message box will pop up, select key servers. There you should have 3 servers by default, you can add any key server you want. Select one to upload your key to, close it and select sync. Should take a moment, and now if someone using ubuntu wants to send you something encrypted, tell them to search for your key(Find remote keys button, search for the name or mail you put in it and hit import) and they can have it now. Another way of sharing your public key is through the export public key button, there select where you want to save it. To import a key from a file, go to key -> import, select it and there you go. But before you can use someone else's key, you have to go to the other collected keys tab, right click the key, properties. Go to the trust tab, and check the I have checked that this key... Do this only if you trust the key came from who you actually think it did.

So what if they don't use ubuntu or you want to encrypt stuff and there's not an ubuntu box near? I found a nice program made in Java to encrypt using pgp([http://sourceforge.net/projects/ppgp/]("http://sourceforge.net/projects/ppgp/")). It's pretty much like the one we just saw but it can be carried around in a USB drive and you can just encrypt from anywhere. Shouldn't be too hard to work with it, and you can import your public key using either method, search a key server or through the key file.

This whole encrypting thing is very nice, but what if for some reason my hard drive is fried and I lose my private key? Well, without private key you can't decrypt something encrypted with your public key, so it would be a good idea to back up your private key. Remember to be very careful where you put this key so only you can access it. Go to Key -> Back up keyrings... Select where you want to save them and what name you want for them. Copy them or upload them wherever you choose and then shred the key file
```
shred -z -u <keyfile>
```

---

### Post by Coder543 on 2009-07-11
Pretty nice, a bit vague in some areas, but the only thing i am commenting on is the use of "shred". Shred does not work on journaled filesystems. (aka. the main filesystems of Ubuntu) This is unfortunate, but true, so shred is ineffective.

---

### Post by Xsoldier2000 on 2009-10-06
Edited

---

### Post by Sarmacid on 2009-10-07
Did you creat the keys with *Passwords and encryption keys* or did you import them? I was having a bit of a problem when I tried to import them in 9.04 but it wasn't a big deal.

---

### Post by bobzxr on 2012-05-27
I created my PGP key, but still cannot encrypt.

Even after system restart, I do not have an encrypt menu if I right click on a file, neither have a text encryption plugin in gedit.

I guess something should be installed?

Update: I installed "decrypt file" (seahorse nautilus) plugin for nautilus. Now I can encrypt from it with right click, but still can't encrypt text within gedit.

---

### Post by oldos2er on 2012-05-27
Old thread closed, please start a new thread for your question.

---

