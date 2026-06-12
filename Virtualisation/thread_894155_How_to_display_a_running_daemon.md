---
title: "How to display a running daemon"
date: 2008-08-19
forum: Virtualisation
---

### Post by satimis on 2008-08-19
Hi folks,


Ubuntu 8.04 desktop amd64 - host
KVM
Ubuntu 8.04 desktop i686 - guest


Running following command on console;```

# kvm ubuntu_i686.img -nographic -daemonize

```

I can run the guest as daemon on the VM working on background.  I'm now looking for a way to make it changed to work from background to foreground without stopping and restart it. Any hint?


Performed following test without success;


Console-1
# kvm ubuntu_i686.img -nographic -daemonize -vnc :0


Console-2
$ vncviewer localhost -geometry 1024x768


only a black screen displayed unable to display the guest.  If without -nographic -damonize then it works displaying the guest on screen.



Performed following steps to kill daemon


Console-1
# kvm ubuntu_i686.img -nographic -daemonize [enter]
#

I can't type on Console-1.  The guest is running as daemon.


Console-2
$ ps -ae | grep kvm
6415 ? 00:00:31 kvm

$ sudo kill 6415


The running daemon killed. I can start ubuntu_i686.img on another console without complaint. However I still can't type on Console-1. I have to close Console-1. 


Advice would be appreciated.  TIA


B.R.
satimis

---

### Post by AjBaz100 on 2008-08-19
find the pid of the process using ps ax and then use the fg command.

---

### Post by satimis on 2008-08-19
> **AjBaz100 said:**
> find the pid of the process using ps ax and then use the fg command.
Hi AjBaz100,


Thanks on your advice.


1)
I don't have fg on my box.  Just have "mtools" installed but still can't find it.  Googling "linux fg command package" can't discover the package.  Please advise which package provides fg.  TIA


2)
Whether run;

$ ps ax | grep kvm

to find its pid number

then;

$ fg "pid number"

to bring the daemon to forground?


B.R.
satimis

---

### Post by satimis on 2008-08-19
Hi AjBaz100,


I found fg but unable making it to work.  It is a shell builtin


Performed following test on a Virtual Machine.

On console
# kvm ubuntu.img -nographic -daemonize

ubuntu.img – guest

I can ping its local IP and ssh connect the guest without problem.

On the same console

# jobs -l```

      [1]+ 6565 Done kvm ubuntu.img -nographic -daemonize
```

# fg 6565```

      bash: fg: 6565: no such job

```

# ps ax | grep kvm```

      6567 ? Sl 0:33 ubuntu.img -nographic -daemonize
      6595 pts/0 S+ 0:00 grep kvm
```


# fg 6567```

      bash: fg: 6567: no such job

```

What is the correct syntax running fg? TIA


B.R.
satimis

---

