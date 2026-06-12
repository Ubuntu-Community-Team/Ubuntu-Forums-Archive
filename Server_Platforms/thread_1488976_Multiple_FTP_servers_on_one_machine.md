---
title: "Multiple FTP servers on one machine?"
date: 2010-05-20
forum: Server Platforms
---

### Post by kornfan71 on 2010-05-20
Hi all,
I'm running Ubuntu Server 10.04 and have a secure (SSL/TLS) FTP server on it. However, I'd like to use this FTP server to update programs I made using Microsoft Visual Studio. Unfortunately, in Microsoft's infinite wisdom, secure FTP servers cannot be used. Rather than use an insecure FTP server, I want to set up my secure FTP server to be able to access whatever I need to on the machine, and then add an insecure FTP server that only has access to the directory where I put my update files.

I am currently using vsftpd as my FTP server. Is there any way that I can set up two FTP servers on this single machine? (Preferably only using vsftpd, if possible.)

Thanks in advance!

---

### Post by kornfan71 on 2010-05-20
Hate to answer my own question, but I found [this]("http://www.redhat.com/docs/manuals/enterprise/RHEL-4-Manual/en-US/Reference_Guide/s2-ftp-vsftpd-start-multi.html"), which is all well and good, except I now ran into another barrier that someone should be able to help with.
I don't know how to work with the upstart crap in Ubuntu 9.10 and up, so how would I go about making a script that could run the command "vsftpd /etc/vsftpd/vsftpd-nossl.conf" at startup, and allow me to start/stop/restart it like a normal upstart job?

I found the documentation for upstart, but suffice it to say that I'm not too adept at shell scripting yet....

Help, please?

---

### Post by scheuri on 2010-05-21
Hi there

First off:
I havent done that myself with FTP, I have dont that ages ago with apache...so....well...sorry if it doesnt help you.

technically you can run thousands of ftp-servers on your linux (no matter if ubuntu or something else).
Point is, that you need to install them (maybe even compile yourself) and then let them listen to a different port (like 8021 or so).
What is not possible is running different ftp-deamons on the same port.

So what you want is installing ftps for your own usage listening to whatever port and then installing (either via apt or compiling) another ftp. The start-script of the other ftp need to be adapted so they listening to another port than your first ftp.

Actually, since ftp and ftps should use different ports it may suffice to install another ftp-only deamon and start it (and of course configure it properly). They shouldnt get into the way of each other, unless the ftps is also using the standard ftp port.

If you install two ftp with atp, the appropriate upstart scripts should be provided. So make a backup and change the ports and configuration...that should do it.
Sorry for not being able to get into details, but I havent done this myself (yet).

Regards
scheuri

---

### Post by kornfan71 on 2010-05-22
Thanks for your response scheuri, but as I stated in my last post, I have found a way to do it, I just cannot figure out how to use upstart to make the command start automatically when I start the machine (I didn't really understand the documentation).

How would I make an upstart script that would run "vsftpd /etc/vsftpd/vsftp-nossl.conf" and would allow me to start/stop/restart it using the "service" command?

---

### Post by ian dobson on 2010-05-22
Hi,

I'm using the standard upstart conf file for my ftp server.

```

# vsftpd - FTP Daemon
#

description     "vsftpd daemon"
author          "Chuck Short <zulcss@ubuntu.com>"

start on (filesystem
        and net-device-up IFACE!=lo)
stop on runlevel [!2345]
respawn

pre-start script
        check_standalone_mode()
        {
                # Return 1 if vsftpd.conf doesn't have listen yes or listen_ipv6=yes
                CONFFILE="/etc/vsftpd.conf"

                if [ -e  "${CONFFILE}" ] && !egrep -iq "^ *listen(_ipv6)? *= *yes" "${CONFFILE}"
                then
                        echo "${CONFFILE}: listen disabled - service will not start"
                        return 1
                fi
        }
        [ -d /var/run/vsftpd ] || install -m 755 -o root -g root -d /var/run/vsftpd
        [ -d /var/run/vsftpd/emply ] || install -m 755 -o root -g root -d /var/run/vsftpd/empty
        check_standalone_mode || exit 0
end script

exec /usr/sbin/vsftpd

```

Maybe if you take this conf file and save it under /etc/init/vsftpd-no-ssl.conf. You'll need to modify afew lines (/var/run bits and CONFFILE=) and add /etc/vsftpd/vsftp-nossl.conf to the exec line.

Regards
Ian Dobson

---

### Post by bodhi.zazen on 2010-05-22
Depending on your needs, you could probably use LXC (Linux Containers) to do this as well.

---

### Post by kornfan71 on 2010-05-24
Thanks for your responses, everyone.
ian dobson's idea worked out great, so I'm just gonna stick with that.
Now I just have to fiddle with that infernal Microsoft software.... ](*,)
Wish me luck.

Thanks again!

---

