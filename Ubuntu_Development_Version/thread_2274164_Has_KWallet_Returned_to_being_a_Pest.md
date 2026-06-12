---
title: "Has KWallet Returned to being a Pest?"
date: 2015-04-18
forum: Ubuntu Development Version
---

### Post by buzzingrobot on 2015-04-18
Anyone know if/when Kwallet will return to its transparent don't-bother-me state on Kubuntu 15.04? It's pestering me for KWallet passwords that I have not created. I can cancel out of that, but then apps like KMail with their own passwords also pester for their passwords.

As I understand it, the "old" version of Kwallet needs to be in place for "old" KDE4 apps, while the a new version ported to '5' also needs to be in place for apps ported to that. 

I'd guess both Kwallet's are in 15.04 since the apps are still a mix of both versions of KDE. Is there a way to convince *both* versions to 'just work' transparently, and stop nagging me to provide a KWallet password before it allows an app to ask for the password KWallet is supposed to have stored in the first place?

For something that should be as transparent as Gnome's keyring, KWallet certainly seems to have a long tradition of annoying and confusing people.

Grumble, grumble... ;)

---

### Post by buzzingrobot on 2015-04-18
Ah, well...  

I closed the Wallet with KWalletManager.  Now, KMail prompts for a password every session and KWalletManager crashes on launch, preventing the Wallet from being opened again.

This seems an annoying bug to persist this close to release. I understand the need to have two version of KWallet to deal with the two different app platforms.  But, KWalletManager and KMail are "old" apps, so users have reason to expect them to continue to work as usual.

---

### Post by oldos2er on 2015-04-19
I stopped using Kmail when KDE went from 3.5 -> 4.x because the changes made to it were detrimental, I thought. Thunderbird doesn't care about kwallet and vice versa. Just FYI.

---

### Post by craig10x on 2015-04-19
When i used kubuntu (kde) i recall that kwallet was always a major pain in the rear :rolleyes:
I'm glad that gnome (and ubuntu) doesn't have that...

---

### Post by buzzingrobot on 2015-04-21
KWallet has actually been well behaved for some time, in my experience. I.e., it stopped prompting for passwords every 5 minutes (and not because the user created blank passwords.)

I suspect in this instance it's to do with Kwallet being ported to the new '5' environment, while the old '4' packages are needed to deal with unported '4' packages that require it. So, for the time being, you get two KWallet front ends and two Kwallet back ends.

---

### Post by buzzingrobot on 2015-04-21
Well, I did a fresh install with today's Kubuntu daily (the live session of that does not work: display sleeps, keyboard is dead). Immediately after the reboot, I launched the Update Manager.  I dialogue popped up asking me to migrate the existing Kwallet to the 'new' Kwallet.  When I told the dialogue to proceed, it prompted me for a Kwallet password, which, of course, I had not created. Canceling out at that point triggered an error message.

Meanwhile, KWalletmanager reports the existence of a 'kdewallet' that is 'closed'.  If I try to open it, I'm again prompted for a nonexistent KWallet password.

Filed a bug about this. 'Tis annoying.

---

### Post by marco-parillo on 2015-04-23
For migrating the empty kwallet on fresh installs, it looks as if it is fixed upstream: [https://bugs.launchpad.net/ubuntu/+source/kubuntu-meta/+bug/1434052](https://bugs.launchpad.net/ubuntu/+source/kubuntu-meta/+bug/1434052)

---

### Post by buzzingrobot on 2015-04-23
> **marco-parillo said:**
> For migrating the empty kwallet on fresh installs, it looks as if it is fixed upstream: [https://bugs.launchpad.net/ubuntu/+source/kubuntu-meta/+bug/1434052](https://bugs.launchpad.net/ubuntu/+source/kubuntu-meta/+bug/1434052)

Thanks!  I imagine it will show up in the first batch of post-release updates.

---

