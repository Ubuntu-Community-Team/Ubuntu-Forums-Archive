---
title: "Help"
date: 2005-10-31
forum: The Cafe
---

### Post by ebonysurfer on 2005-10-31
I am new period  I can't even get the new section to work :(  I have loaded ubuntu at least five times trying to use root and still can't even after reading directions and yes i have the password right.

---

### Post by Sheco on 2005-10-31
Ubuntu doesn't setup the root account, it sets up a normal user account and you don't log directly into root, but you can run everything with sudo.

Log in as the user you created and when you need to run something as root do:
sudo {command}

where {command} is the command you want to run.

if you desperately need a root shell, you can do
sudo sh

---

