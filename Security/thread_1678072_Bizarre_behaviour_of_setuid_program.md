---
title: "Bizarre behaviour of setuid program"
date: 2011-01-29
forum: Security
---

### Post by crankycanuck on 2011-01-29
Hello,

I have looked through the forum and had no luck, so I thought I'd try posting a new thread.  If I've overlooked something, my apologies.  Feel free to apply the clue-by-four.

I have an Ubuntu 10.10 system on which I need to be able to start certain daemons (in this case, name servers) as a non-root user.  The action is triggered from a web service.  Obviously, to be able to bind to port 53, the daemon needs to be root.  

The daemon is in a chroot.  So (to stick with BIND because people probably know that one best), the call would be something like this:

 ```
/path/to/named -u the_user_name -t /path/to/chroot -c /etc/named.conf
```

I have a little program that runs setuid root and starts (for instance) named.  I would expect this to work.  But named starts up, but the daemon can't bind to any interfaces.  One sees things like this in syslog:

```
Jan 28 18:32:07 cloud named[8484]: listening on IPv4 interface lo:3, 10.4.7.3#53
Jan 28 18:32:07 cloud named[8484]: could not listen on UDP socket: permission  denied                                                                         
Jan 28 18:32:07 cloud named[8484]: creating IPv4 interface lo:3 failed; interface ignored                                                              
Jan 28 18:32:07 cloud named[8484]: listening on IPv4 interface lo:4, 10.4.7.4#53
Jan 28 18:32:07 cloud named[8484]: could not listen on UDP socket: permission denied                                                                         
Jan 28 18:32:07 cloud named[8484]: creating IPv4 interface lo:4 failed;   
```

and so on.

I initially thought that there was something wrong with the wrapper program, so I tried this:

 ```
sudo /path/to/named -u the_user_name -t /path/to/chroot -c /etc/named.conf
```

But I get the same result.  However, if I log into a root shell and start the process using the same command line (i.e. /path/to . . . etc.), named comes up just fine and the target user has control via rndc of the server.

I've disabled apparmour completely, thinking it might make a difference, but no dice.  This program works as I expect on FreeBSD.  I'm sure I'm overlooking something dumb, but I'm stumped.  Any suggestions?

Thanks,

Andrew

---

### Post by The Cog on 2011-01-30
Does /path/to/named point to a shell script or a binary executable? I wonder if you have hit a little security gotcha - setuid root only works on binaries - not scripts. If this is your problem, the only way round it that I know of is to compile a small binary that then calls your script. 

Here's an example that restarts the ssh daemon. Create a file with these contents:```
int main(int argc, char** argv) {
    system("/etc/init.d/ssh restart");
}

```Compile it to make the test binary:```
sudo apt-get install build-essential
gcc -o test test.c
```Change the permissions:```
sudo chown root:root test
sudo chmod 4755 test
```Then you can run it as a normal user.```
./test
```

---

### Post by crankycanuck on 2011-01-30
> **The Cog said:**
> Does /path/to/named point to a shell script or a binary executable?

Thanks for your reply.  No, this is a C program written precisely because you can't run shell scripts setuid root.  It's a slightly more complicated version of the code you posted (depending on the calling user, different nameserver daemons get selected, but other than that it is the same, using the system() call).  

My working hypothesis is that this has something to do with threads on Linux.  It's the only difference I can think of that might make the difference between Linux and FreeBSD.  But I thought all the threading issues were worked out in recent kernels, and I haven't run across anything like this recently.  

The only other thing I thought might be relevant is all the special devices:

```

proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

```

But that seems preposterous.  I'm really stumped.

Thanks for your help!

---

### Post by crankycanuck on 2011-02-15
Hi,

I realised that I forgot to update this.  But I found (sort of) a solution.

It turns out that if you compile BIND with --disable-threads, it works.  This is sort of strange, since the configure script seems to suggest that they're off by default, but unless you explicitly set this switch, you get the unexpected behaviour.

There is the question of whether there is a performance hit from having threading turned off.  I don't know.

---

