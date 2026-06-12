---
title: "Apparmor RBAC issue"
date: 2012-12-12
forum: Security
---

### Post by sgm277 on 2012-12-12
Hi All,

I would like to use Apparmor to confine a user that just has the permission to restart apache2 like I did in Cetnos via using Selinux successfully.

I created a hard link of SHELL and used aa-genprof /bin/ashell and updated it using aa-logprof. 

Then edited the sudo file.

user ALL=(ALL:ALL) /bin/ashell

Everything worked fine.

But later I found a problem that the user can kill processes whose owner are root.

Bellow is the profile:

#include <tunables/global>

/bin/ashell{
  #include <abstractions/apache2-common>
  #include <abstractions/base>
  #include <abstractions/ubuntu-konsole>

  capability dac_override,
  capability setgid,
  capability setuid,
  capability sys_ptrace,
  capability sys_resource,



  /bin/cat rix,
  /bin/grep rix,
  /bin/lesspipe rix,
  /bin/ls rix,
  /bin/mkdir rix,
  /bin/plymouth rix,
  /bin/rm rix,
  /bin/sed rix,
  /bin/sleep rix,
  /bin/songbash mr,
  /bin/uname rix,
  /etc/apache2/apache2.conf r,
  /etc/apache2/conf.d/ r,
  /etc/apache2/conf.d/* r,
  /etc/apache2/envvars r,
  /etc/apache2/httpd.conf r,
  /etc/apache2/mods-available/* r,
  /etc/apache2/mods-enabled/ r,
  /etc/apache2/ports.conf r,
  /etc/apache2/sites-available/default r,
  /etc/apache2/sites-enabled/ r,
  /etc/bash.bashrc r,
  /etc/bash_completion r,
  /etc/bash_completion.d/ r,
  /etc/default/apache2 r,
  /etc/default/rcS r,
  /etc/init.d/apache2 rix,
  /etc/inputrc r,
  /etc/lsb-base-logging.sh r,
  /etc/mime.types r,
  /home/*/.bash_history rw,
  /home/*/.bashrc r,
  /proc/ r,
  /proc/*/cmdline r,
  /proc/*/stat r,
  /proc/cmdline r,
  /run/apache2.pid rw,
  /run/apache2/ r,
  /run/apache2/cgisock.14207 w,
  /run/apache2/cgisock.14258 w,
  /run/apache2/cgisock.14300 w,
  /run/lock/apache2/ r,
  /sbin/killall5 rix,
  /usr/bin/basename rix,
  /usr/bin/dircolors rix,
  /usr/bin/dirname rix,
  /usr/bin/env rix,
  /usr/bin/expr rix,
  /usr/bin/groups rix,
  /usr/bin/install rix,
  /usr/bin/tput rix,
  /usr/bin/tr rix,
  /usr/lib/apache2/mpm-worker/apache2 rix,
  /usr/lib{,32,64}/** mr,
  /usr/sbin/apache2ctl rix,
  /usr/sbin/service rix,
  /usr/share/GeoIP/GeoIP.dat r,
  /var/log/apache2/access.log w,
  /var/log/apache2/error.log w,
  /var/log/apache2/other_vhosts_access.log w,
  /var/log/apache2/write.log w,

}

What is wrong with the profile? 
Thanks,

---

### Post by Hungry Man on 2012-12-12
The ability to kill those processes is given by Sys_Ptrace I assume. Ptrace is an incredibly powerful capability, allowing the process to control another, and I would assume giving it the ability to kill it.

---

### Post by sgm277 on 2012-12-12
> **Hungry Man said:**
> The ability to kill those processes is given by Sys_Ptrace I assume. Ptrace is an incredibly powerful capability, allowing the process to control another, and I would assume giving it the ability to kill it.

Thanks for the prompt reply, after sudo, the user can kill the processes only belong to root, for ntp process, user can't kill it.

Even I set "deny /bin/kill x," and "  deny capability kill,", the user still can use kill command.

---

### Post by Hungry Man on 2012-12-12
Not sure. I can only guess, really, but I figure that's better than nothing. Allow rules in AppArmor override Deny rules, so if the sys_ptrace capability grants it access to kill the process it might not make a difference if you deny reading 'kill'. sys_ptrace is arbitrary though, at least on a vanilla kernel as far as I know, so I'm not sure why you could kill root but not NTP.

Would it by possible to temporarily remove the sys_ptrace capability and then see if you can still kill the root process?

I checked the abstractions and didn't see anything too bad. Though one of them does also include ptrace, the console one. So i'd comment that out temporarily when testing.

---

### Post by sgm277 on 2012-12-12
I commented out sys_ptrace but after running sudo the user still could kill process like ssh whose owner is root.

For ntp because the owner of this process is ntp, so when I killed ntp ID manually, I got "Operation not permitted".

---

