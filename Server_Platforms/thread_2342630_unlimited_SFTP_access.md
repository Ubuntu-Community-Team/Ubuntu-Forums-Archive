---
title: "unlimited SFTP access"
date: 2016-11-08
forum: Server Platforms
---

### Post by chrisscottuk on 2016-11-08
Hi there,

I have already searched the forums and surprisingly have bene unable to achieve this.
I use Ubuntu 16.04LTS and need to grant a new user - full SFTP permissions and SSH permissions so that they can logon to my server and access any folder or file (like I can).

When I create a new user for them, even though I've added them to SUDO, it seems to restrict their access to their own user folder, which isn't what I need.

They need access to help me with a tech problem, but I don't want to share my own log on with them. 

Could someone explain in simple (newbie) terms how I can achieve this? I'd be most grateful

Kind Regards,
Chris

---

### Post by darkod on 2016-11-08
If you added them to the sudo group there is no way that they don't have access to all the system. I assume they know how to use sudo, right? Just to make sure, you as admin can add any user to sudo group with:
```
sudo usermod -aG sudo <username>
```

That will add the user 'username' to have sudo permissions, in other words, can act as root. And root has total access to linux systems.

When they log in, it is normal the first thing to open to be their home folder, but when using ssh session if they do 'sudo -i' they can become root. After that they can open what ever they want.

For sftp it might be little more complicated and it might depend on the client they are using to connect. Because usually you wouldn't be able to login directly as root, you have to use your user. And it will depend on the sftp client if they can somehow change the login inside the session.

But for ssh, it works perfectly.

PS. What I usually do when needing to move files as root, I upload the files with my standard user by sftp/scp to my home folder. After that I connect by ssh session and with sudo I can do what I need with the files. For me it's less complicated than setting up full sftp access and depend if the client can log me in directly to the path I need...

---

