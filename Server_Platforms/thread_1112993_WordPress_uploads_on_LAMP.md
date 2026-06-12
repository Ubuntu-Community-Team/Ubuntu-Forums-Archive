---
title: "WordPress uploads on LAMP"
date: 2009-04-01
forum: Server Platforms
---

### Post by itsonlybarney on 2009-04-01
I'm running Ubuntu 8.04.1 as my webserver, using Apache 2.2, php5, and MySQL5.

I have 4 domains running as virtual hosts, and 3 of the sites are running WordPress 2.7.1

The problem I am experiencing, is that one of the sites allows WordPress to upload files to the server when the wp-content/uploads folder has the permissions set to 777.  When I setup another one of the virtual hosts, with the exact same permissions, WordPress says that the files can't be uploaded, and to check the owner of the folders.

I can't work out why the same configuration works on one virtual host, but not the other, even though they are identical.

Any ideas would be totally appreciated.

---

### Post by itsonlybarney on 2009-04-02
Nevermind, I figured out what the problem was. However, is there a way to go about it so that I don't have to have my permissions set at 777? I was told that this can possibly open my server up to unwanted problems.

---

### Post by tr33m4n on 2009-04-03
On a folder like that, what I would do is set the permissions to 775 and set the owner of the folder to yourself, but the group to 'www-data'... that way the server will be able to read/write to the folder, yet you can restrict access to other users. Anybody else have any other ideas? is my way still unsecure?

Cheers
Dan

---

### Post by 720iD on 2009-06-07
> **tr33m4n said:**
> On a folder like that, what I would do is set the permissions to 775 and set the owner of the folder to yourself, but the group to 'www-data'... that way the server will be able to read/write to the folder, yet you can restrict access to other users. Anybody else have any other ideas? is my way still unsecure?

Cheers
Dansounds good i will give that a try thanks.

---

