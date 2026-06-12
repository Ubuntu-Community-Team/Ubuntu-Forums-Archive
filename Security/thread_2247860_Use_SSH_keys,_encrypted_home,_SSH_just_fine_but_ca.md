---
title: "Use SSH keys, encrypted home, SSH just fine but can not access home"
date: 2014-10-10
forum: Security
---

### Post by MechaMechanism on 2014-10-10
I should restate this another way.  I can SSH into my box.  I just want  to automate the proccess of manually mounting my encrypted home.  When I  SSH into to the box, home is not mounted and so I have to manually  mount and decrypt the home dir.

I can SSH just fine into my machine.  However /home/nate/ is encrypted.  I tried some ideas off the net and still can't access nate.

I created a .profile file in /home/ and it looks like this:
ecryptfs-mount-private
cd /home/nate/

I got the profile thing from here: [http://askubuntu.com/questions/115497/encrypted-home-directory-not-auto-mounting](http://askubuntu.com/questions/115497/encrypted-home-directory-not-auto-mounting)

From that page someone said, 
To solve this, you'll need to add a line to the end of your *unmounted* $HOME/.profile:
  ecryptfs-mount-private
  This will ensure that after you've logged in using SSH Public Key  authentication, you'll be prompted for your password and will mount your  encrypted data.  If it's already mounted, then this command should just  silently succeed.

Someone else said, Awesome, thanks, that does exactly what I want I had to add cd /home/$HOME into the .profile file as well, to refresh it though once it had decrypted.

Can you please help me.

---

### Post by ecophobia on 2014-10-11
Probaby should check [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys) under
[h=1]Troubleshooting[/h][LEFT][COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR][/LEFT][h=3]Encrypted Home Directory[/h]

---

### Post by MechaMechanism on 2014-10-11
Thanks for the reply.  I did check there.

I should restate this another way.  I can SSH into my box.  I just want to automate the proccess of manually mounting my encrypted home.  When I SSH into to the box, home is not mounted and so I have to manually mount and decrypt the home dir.

---

### Post by ecophobia on 2014-10-11
Not 100% sure, but I would check ~/.profile' to see if 'ecryptfs-mount-private' is there.

---

