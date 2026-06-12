---
title: "how to ssh/scp without having to enter password each time?"
date: 2009-05-06
forum: Security
---

### Post by sa125 on 2009-05-06
Hi -

I find that I need to ssh/scp to remote machine quite a bit, and it's quite annoying to enter a password every time I do so (hourly basis). I know there's a way to authenticate a connection with a key file (ssh-keygen -t rsa), but I'm not sure what needs to be saved where on the remote machine. I'd appreciate a very brief walk through to help clarify this, like:
1. create keyfile with $ ssh-keygen -t <rsa|dsa>
2. copy the pub file to ...

Thanks!

---

### Post by Kobalt on 2009-05-06
Hello,

See this for some guidance : [https://help.ubuntu.com/community/AdvancedOpenSSH#RSA%20Key-Based%20SSH%20Logins](https://help.ubuntu.com/community/AdvancedOpenSSH#RSA%20Key-Based%20SSH%20Logins)

---

### Post by bodhi.zazen on 2009-05-06
> **sa125 said:**
> Hi -

I find that I need to ssh/scp to remote machine quite a bit, and it's quite annoying to enter a password every time I do so (hourly basis). I know there's a way to authenticate a connection with a key file (ssh-keygen -t rsa), but I'm not sure what needs to be saved where on the remote machine. I'd appreciate a very brief walk through to help clarify this, like:
1. create keyfile with $ ssh-keygen -t <rsa|dsa>
2. copy the pub file to ...

Thanks!

Use ssh-agent

You then use ssh-add , add your key , enter your password.

As long as your session is open, you then simply

ssh -i ~/.ssh/key user@server

---

### Post by slakkie on 2009-05-06
This is pretty simple to do:

ssh-keygen like you suggested

ssh-copy-id $machine will copy the public key to the remote box and you should have a passwordless connection.

---

### Post by sa125 on 2009-05-07
Thanks for all of those - I'll try them and see which one works for me.

---

### Post by lensman3 on 2009-05-07
On one line do:

cat ~/.ssh/id_rsa.pub | ssh user@remotebox "(mkdir .ssh&>/dev/null; chmod 700 .ssh && cat - >> .ssh/authorized_keys )&&chmod 600 .ssh/authorized_keys"

Just change the user@romotebox.  When you run this it will prompt for the password the first time, because it has to login and append to the authorized_keys file.  After that no password required.  This little script creates the hidden directories and changes the file permissions to the correct mode.  Works fine if the .ssh hidden directory already exists.  The only real gotcha is that you must be in the home directory of the user that is being setup.  "cd" by itself on a line takes you to your home directory, the tilde's ~.

Setup the RSA encryption as earlier.

ssh-keygen -t rsa

Hope this helps.

---

