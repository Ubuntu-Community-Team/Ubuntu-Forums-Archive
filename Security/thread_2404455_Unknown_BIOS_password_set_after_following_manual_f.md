---
title: "Unknown BIOS password set after following manual full encryption instructions ?"
date: 2018-10-24
forum: Security
---

### Post by user188480 on 2018-10-24
I was trying to setup Ubuntu 18.04 / Windows 10 dual boot with full disk encryption of the Ubuntu partitions by following this guide:
[https://help.ubuntu.com/community/ManualFullSystemEncryption](https://help.ubuntu.com/community/ManualFullSystemEncryption) by Paddy Landau ([https://ubuntuforums.org/member.php?u=572807](https://ubuntuforums.org/member.php?u=572807)).
I am using a Lenvo Thinkpad with pre-installed win 10.
Everything was like it is described in the guide until the point where I was supposed to restart the system and when I was trying
to boot into Ubuntu I ran into the problem described here: [https://ubuntuforums.org/showthread.php?t=2398512](https://ubuntuforums.org/showthread.php?t=2398512), i.e.
when I try to startup ubuntu I get an error 'you need to load the kernel first'. As described there this is apparently expected, because I forgot to disable
Secure Boot as it is mentioned at the very beginning of the instructions.
I then went into my BIOS where I was asked for a password. The problem is to the best of my knowledge I have never setup a password in the BIOS/EFI. 
The only thing I can do is press enter, but this only opens BIOS in read-only mode (for example I cannot disable secure boot).
I remember in the Ubuntu installer I was supposed to allow 3rd party installation (Step 2.3 here: [https://help.ubuntu.com/community/ManualFullSystemEncryption/DetailedProcessInstallUbuntu](https://help.ubuntu.com/community/ManualFullSystemEncryption/DetailedProcessInstallUbuntu)) and the installer then asked me to enter a (temporary ?) password for secure boot. I did enter a password there and it included
some non-alphabetic characters (a dot '.' to be precise). I was hoping the BIOS would accept the password I entered there, but first of all it does not let me
type dots at all (it only beeps if I press the dot button) and the password is not accepted either if I leave out the dot. I am a bit lost now and my most urgent 
questions are:

- could it be that because I followed the manual installation instructions a BIOS (supervisor) password was set ? 
- if yes is it supposed to be the password I entered in the dialog where I was asked to install 3rd party software ?
- what is supposed to happen if this password contains special characters and I cannot enter them in BIOS ?
- is there any other mechanism that could have set the BIOS password (except someone opening BIOS and setting up a 
  supervisor password) ?
- is it possible to find out when the supervisor was set ? I do not own this computer for long and since I haven't used the
  BIOS before this I cannot tell if the password was set when I got the computer already
- any other suggestions what I can do ?

Thanks in advance !

---

### Post by oldfred on 2018-10-24
What brand/model system?
Was it a proprietary driver install that asked for the password?

It used to be that you just turned off UEFI Secure Boot before installing any proprietary drivers. But recently they have changed some things, not sure of details.

In old days we could totally reset BIOS and all settings reverted to defaults. But with new UEFI, not sure what settings are saved and what are reset.
With my system a update to UEFI resets settings, but I have Secure Boot off and have to turn it off again. But it does remember the UEFI boot entries.
So you might be able to either totally reset UEFI or install new UEFI. But you probably need password to get into UEFI to install new UEFI. A few systems now allow UEFI updates from within Ubuntu. 
If desktop you can jumper pins on motherboard or remove coin battery for a bit to totally reset system. Laptops often are the same, but access more difficult.

---

### Post by user188480 on 2018-10-24
Turns out I must have somehow set the BIOS pw in the past..

---

