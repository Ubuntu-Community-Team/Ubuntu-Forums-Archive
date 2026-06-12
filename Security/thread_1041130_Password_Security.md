---
title: "Password Security"
date: 2009-01-16
forum: Security
---

### Post by Kissell on 2009-01-16
I've seen some how-to's that explain how to use PAM to automatically mount an encrypted volume, but to do that you have to make your luks key the same as your linux user password...  

That seems like it may be insecure to me...  how secure is the password security in Ubuntu?  like for my linux user account?  is it just as secure as a luks key?

---

### Post by Tubes6al4v on 2009-01-16
Do you want to automount your drive on boot? is it Full Disk encryption? What encryption software is it? LUKS?

If you just want to avoid typing in a long passphrase you could use a keyfile.

---

### Post by Kissell on 2009-01-16
I'm using luks on a data partition...  and i like the idea of using the password I login with to unlock the partition, so that it'd be unlocked when I login and not unlocked for others and i wouldn't have to do anything extra to unlock it...  

my concern is that if someone took my laptop, would it be easier for them to hack my linux password if it were the same length and complexity as my luks passphrase?  because if they can hack my linux password then they gain access to my luks encrypted data...  but, if i just use the passphrase and don't use pam to unlock it, then i'm fairly confident in that security... but I'm just not as confident in the linux user account security, which if compromised makes the other accessible if they're linked...  so that's what i'm wondering, how secure is the linux user account security if the password is a good long one?  am I safer NOT using the linux user account password to unlock my disk?

---

### Post by Dr Small on 2009-01-16
> **Kissell said:**
> so that's what i'm wondering, how secure is the linux user account security if the password is a good long one? 

I have a 10 character password (quite difficult with random case, punctuation, etc) and I set John the Ripper on it for 2 weeks. Yes, 2 weeks, and he never cracked it. I would say that if you use a fairly complex password, it won't be cracked anytime soon.

---

### Post by Kissell on 2009-01-16
Yeah, if you use a long enough password then it'll take forever to brute force hack it...  

but i'm just concerned with the security of the linux user account password...  I know luks is pretty secure, but maybe there could be an exploit to how the linux user account stores its password, if it's encryption isn't as strong as the 256-bit AES cipher ESSIV used in luks, then wherever linux stores its password for your user account would be a LOT easier target to hack...  someone boots to a live cd and hacks your linux user account password, then they have full access to the secure encrypted data partition because you tied your linux account to it...  

I don't know for sure if the linux password is less secure, i was just wondering if anyone knew for sure...  I suspect it is much less secure, and therefore auto-mount via PAM authentication to luks is a bad idea.

---

### Post by hyper_ch on 2009-01-16
what exactely do you want to do?

---

### Post by Kissell on 2009-01-16
I want to login to my computer and have it automatically unlock my encrypted drive...  

i have it doing that...

what i want to know, is have i lessened my security by doing that, because I had to make the key for the encrypted partition the same as my linux user account password for this to work...

so if the linux user account password is store less securely, then i have lessened my security and should stop using this method.

I don't really want to do anything, I'm wanting to know how much (if any) my security has been weakened by making the key the same as my user account.  If someone had physical access to my box without me around, they still couldn't hack my encryption, but could they potentially hack my linux user account password, which would give them access to my encrypted data?

---

### Post by hyper_ch on 2009-01-16
generate a key, add the key to the luks device, setup crypttab with they key, set the device in the fstab...

---

### Post by Kissell on 2009-01-16
right, but if i do that, then it's not as elegant...  i get prompted at the text-only screen at boot up, which is confusing to those who don't know the passphrase, and then i still have to enter my unix password...  so i have to enter two passwords...  and i don't like storing the key in a file, i like to keep it in my mind, because it can't be found there by anyone but me. 

So ideally, the really nice and elegant solution would be to use the PAM authentication module to mount the encrypted partition using my linux user account password as the key...  two birds, one stone...  but I don't know if that's less secure or not...  that's what i want to know.  If it's not less secure, then I definately prefer that solution, but i don't want to have all this nice security for nothing if the linux password security is fairly easily hackable compared to the disk encryption.

---

### Post by hyper_ch on 2009-01-16
you would do that only if the root is also encrypted...

---

### Post by Kissell on 2009-01-16
ok, thanks...  that's what i was thinking...  

i typically don't encrypt the root, because it was the data i really cared about, i normally just encrypt the data and the swap...

---

### Post by kojakk00 on 2009-01-16
> **Kissell said:**
> I've seen some how-to's that explain how to use PAM to automatically mount an encrypted volume, but to do that you have to make your luks key the same as your linux user password...  

That seems like it may be insecure to me...  how secure is the password security in Ubuntu?  like for my linux user account?  is it just as secure as a luks key?


Password security in Ubuntu seems to be a joke generally. For example, you can boot to recovery console as root without any password.

---

### Post by Biochem on 2009-01-16
> **kojakk00 said:**
> Password security in Ubuntu seems to be a joke generally. For example, you can boot to recovery console as root without any password.

But to be able to boot to recovery console you need physical access to the computer. If you have such an access nothing prevent you from booting a live cd. That is why recovery console is not protected with a password by default in Ubuntu. However, you can put a root password and it will be ask before entering recovery mode. 

In any case, it has nothing to do with password security.

---

### Post by movieman on 2009-01-16
> **Kissell said:**
> I know luks is pretty secure, but maybe there could be an exploit to how the linux user account stores its password, if it's encryption isn't as strong as the 256-bit AES cipher ESSIV used in luks, then wherever linux stores its password for your user account would be a LOT easier target to hack.

Except Linux doesn't store passwords, it stores hashes of passwords; so they're back to brute-force searching for the correct password against the hash value... and, even then, since an infinite number of possible strings match each hash value, they still can't tell if that password is the correct one to use for the disk.

---

### Post by hyper_ch on 2009-01-17
there are multiple places where (fragments of) files are stored... if you're worried about physical access, go for full disk encryption.

---

