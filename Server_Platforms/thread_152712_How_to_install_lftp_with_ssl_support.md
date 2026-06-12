---
title: "?How to install lftp with ssl support"
date: 2006-03-30
forum: Server Platforms
---

### Post by olddog on 2006-03-30
I set up a file server in our office following the excellent guide at:

[http://www.howtoforge.com/samba_setup_ubuntu_5.10](http://www.howtoforge.com/samba_setup_ubuntu_5.10)

We will use the server for daily archives of our important files and databases.
Each night I want to send the archives to Morrack's backup server ([www.morrack.com)](www.morrack.com)), which uses a ftps server. I understand lftp is a solid ftp-client that can handle scheduling, etc., all from the command line... but it appears that the ubuntu package wasn't compiled with ssl support. I've read the other two threads that bemoan this, but am asking if anyone has had any success, or could tell me in CLEAR, SIMPLE terms, how to solve this.

Thanks in advance for any and all help!

---

### Post by XplOzIOn on 2007-03-19
Well sometimes when Ubuntu repos has old version, etc. I tend to active my debian repos and disable the ubuntu ones :) so far with the apps i have installed theres no problems, i just do a apt-get 'package' nothing else. Not update or upgrade. So far it has working for me without bugs :)

I know it is not the best option, but works when you in a rush and have no time to compile from source. Good Luck

---

