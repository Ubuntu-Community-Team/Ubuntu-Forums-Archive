---
title: "[SOLVED] honeypot setup"
date: 2008-09-16
forum: Security
---

### Post by cdenley on 2008-09-16
I was thinking about setting up a honeypot, but haven't decided on the specifics. I was thinking about keeping disk changes non-persistent so I could start fresh by rebooting, but then attackers would be able to install a new bootloader, right? Now I'm thinking about setting up chroot environments, maybe one per host. Is it possible/easy for an attacker to break out of a jail?

Something else I was thinking about doing was creating a shell to replace or interface with bash, which I could interrupt and interact with. Like in "The Matrix" when his computer starts talking to him. Is there something like this already programmed? Does anyone have any other fun ideas for playing with script kiddies?

Also, I'm unsure of what to do with outgoing internet traffic. It would be a bit irresponsible to allow them to attack other servers from my honeypot, not to mention I might get blamed. On the other hand, they may very well try downloading their hack tools, and when they realize outgoing connections are filtered but incoming are open, it might be obvious they are in a honeypot.

---

### Post by Kinstonian on 2008-09-16
I ran my honeypot in VMWare.  I was monitoring the network traffic.  After I got hacked I waited a while and then took a snapshot so I could revert back to the snapshot at any time.

You're right about not wanting to be liable for damages if your honeypot is used to attack other computers.  I used the roo "honeywall" from the Honeytnet Project, which uses Snort to detect and modify outgoing attacks so they don't work.  It also uses connection rate limiting amoung other things.

[www.honeynet.org](www.honeynet.org) for more info.

---

### Post by cdenley on 2008-09-17
I'm making progress
```

#!/usr/bin/env python

import os, sys, time, getopt
import signal, fcntl, termios, struct
import traceback
import pexpect

global_pexpect_instance = None # Used by signal handler

def ParseChroots():
    ret=[]
    f=open("/etc/schroot/schroot.conf","r")
    try:
        for line in f:
            line=line.strip()
            end=line.find("#")
            if end>-1:
                line=line[:end]
            start=line.find("[")+1
            if start>0:
                end=line.find("]",start)
                ret.append(line[start:end])
    finally:
        f.close()
    return ret

def NewDir(path):
    if os.path.isdir(path):
        return True
    os.mkdir(path)
    return os.path.isdir(path)

def Mount(name):
    NewDir("/opt/honeypot/"+name)
    NewDir("/opt/honeypot/"+name+"/rw")
    NewDir("/opt/honeypot/"+name+"/union")
    if os.path.ismount("/opt/honeypot/"+name+"/union"):
        return True
    os.system("mount -t unionfs -o dirs=/opt/honeypot/"+name+"/rw=rw:/opt/honeypot/master=ro none /opt/honeypot/"+name+"/union")
    return True

def NewChroot(name):
    ret=False
    f=open("/etc/schroot/schroot.conf","a")
    try:
        f.write("\n["+name+"]\n")
        f.write("description=honeypot\n")
        f.write("location=/opt/honeypot/"+name+"/union\n")
        ret=True
    finally:
        f.close()
    return ret

def main():
    chroot="default"
    chroot_dir="/opt/honeypot/master/"
    if len(sys.argv)>1:
        chroot=sys.argv[1]
    create=True
    for name in ParseChroots():
        if name==chroot:
            create=False
    if create:
        NewChroot(chroot)
    Mount(chroot)
    shell="/bin/bash"
    home="/root"
    f = open(chroot_dir+"etc/passwd")
    try:
        for line in f:
            parts=line.split(":")
            if parts[0]=="root":
                shell=parts[6]
                home=parts[5]
    finally:
        f.close()
    if os.path.isfile("/opt/honeypot/"+chroot+"/rw/etc/passwd"):
        f = open("/opt/honeypot/"+chroot+"/rw/etc/passwd")
        try:
            for line in f:
                parts=line.split(":")
                if parts[0]=="root":
                    shell=parts[6]
                    home=parts[5]
        finally:
            f.close()
        
    ######################################################################
    # Start the interactive session
    ######################################################################
    fout=open("log.txt","w")
    p = pexpect.spawn("/usr/bin/schroot -q -d "+home+" -c "+chroot+" "+shell)
    p.logfile = fout
    global global_pexpect_instance
    global_pexpect_instance = p
    signal.signal(signal.SIGWINCH, sigwinch_passthrough)
    try:
        p.interact()
    except OSError, e:
        pass
    fout.close()
    return 0

def sigwinch_passthrough (sig, data):

    # Check for buggy platforms (see pexpect.setwinsize()).
    if 'TIOCGWINSZ' in dir(termios):
        TIOCGWINSZ = termios.TIOCGWINSZ
    else:
        TIOCGWINSZ = 1074295912 # assume
    s = struct.pack ("HHHH", 0, 0, 0, 0)
    a = struct.unpack ('HHHH', fcntl.ioctl(sys.stdout.fileno(), TIOCGWINSZ , s))
    global global_pexpect_instance
    global_pexpect_instance.setwinsize(a[0],a[1])

if __name__ == "__main__":
    try:
        main()
    except SystemExit, e:
        raise e
    except Exception, e:
        print "ERROR"
        print str(e)
        traceback.print_exc()
        os._exit(1)

```

This script creates a unionfs mount using a master chroot environment. It then launches bash within their unionfs chroot. Everything they see in the terminal is logged outside their chroot environment.

They can make all the changes they want, because the master chroot is read-only from their mount. The extra benefit is I can see all the files they change by looking in their rw directory. Now I have to figure out how I could determine the attackers IP from this script when it is set as shell, so each attacker can have their own unionfs chroot. I think I might have to patch openssh to pass the IP as an argument to this shell script.

A concern I had is that the chroot and host environments seem to share iptables rules. I guess I will have to add a script to cron which clears the iptables rules so attackers can't take my honeypot offline for long.

Of course, if they tried, they could determine that they are in a chroot environment. They wouldn't be able to tell as easily if I mount /proc or /dev, but then I think that will give them too much access to the host environment. Any ideas for making the chroot a more complete environment without compromising security? Is there a devfs or procfs emulation or anything? I don't think virtual machines are a possibility, because I couldn't let multiple attackers share the same master machine while keeping their changes seperate unless I made copies of the entire machine. Also, it's a little difficult to control virtual machines from scripts, log shell usage, etc.

---

### Post by cdenley on 2008-09-18
It is actually really easy to break out of a chroot.
[http://www.bpfh.net/simes/computing/chroot-break.html#break](http://www.bpfh.net/simes/computing/chroot-break.html#break)
I'm surprised nobody replied with that information. I guess I will be abandoning my previous script and the whole chroot idea. Now, maybe I will create an SSH server which gives users a fake shell, emulating enough functionality to at least annoy script kiddies and see what they might have done.

---

### Post by HermanAB on 2008-09-18
Yes, chroot is *not* a security feature.  Using chroot to 'secure' a service is a waste of time. However, there are lots of people who disagree and insist on using chroot to 'secure' BIND or SSH and there is no way that your I will ever convince them otherwise.

Cheers,

Herman

---

### Post by cdenley on 2008-09-18
> **HermanAB said:**
> Yes, chroot is *not* a security feature.  Using chroot to 'secure' a service is a waste of time. However, there are lots of people who disagree and insist on using chroot to 'secure' BIND or SSH and there is no way that your I will ever convince them otherwise.

Cheers,

Herman

I think there are some security applications for a chroot. I remember when I was in college, every student had shell access to an ssh server. I, and any spammer with a student login, were able to look at every single student account by reading /etc/passwd. If I were chroot'ed, I wouldn't have been able to read that file. I think you could limit access like that with a restricted shell, though.

I would think when you can show them the code to break out of their chroot, they would see the inherent security flaw. I wonder if other OS's like the BSD's have better jailing techniques. I think OpenBSD has many services jailed by default.

In Linux, root access in a chroot is the same as root access outside a chroot. Using a chroot or not, all a local attacker has to do is escalate privileges to own your system.

---

### Post by cdenley on 2008-09-25
> **cdenley said:**
> Now, maybe I will create an SSH server which gives users a fake shell, emulating enough functionality to at least annoy script kiddies and see what they might have done.

It looks like this has already been done (as I'm putting the finishing touches on my own script).
[http://kojoney.sourceforge.net/](http://kojoney.sourceforge.net/)
It doesn't seem to emulate too many commands, though.

---

