---
title: "Why isn't LD_LIBRARY_PATH inherited by the &quot;at&quot; command?"
date: 2009-07-16
forum: Security
---

### Post by rbpember on 2009-07-16
I just used the "at" command for the first time in my life today:

%coot 23: at 4:00 PM
warning: commands will be executed using /bin/sh
at> myexe
at> <EOT>
job 52 at Fri Jul 17 16:00:00 2009
%coot 24: 

(I've been sheltered most of my life by caring sysadmins who never gave "at" privileges to mere  mortals like me :wink: )

myexe executes just fine from the interactive shell, but using "at" I get an error message from myexe:

/home/pember/bin/myexe: error while loading shared libraries: libguide.so: cannot open shared object file: No such file or directory

Yes, I'm using Intel compilers, and, yes, in my .cshrc I am setting LD_LIBRARY_PATH to include the directory containing libguide.so.  If I use "at -c <jobid>" to examine the status of my job, however, I see that LD_LIBRARY_PATH is not included in the environment for myexe, although all my other environment variables are.

I understand the workarounds. For me, the simplest things were to just put a copy to libguide.so in  /home/pember/bin, or to define LD_LIBRARY_PATH in a script that also execute myexe. What I would like know is: why is this necessary.  

I came to this forum because I did find one terse reference on the web to this being a security problem. Without giving away the store (I don't want to exploit this, I just want to understand) can someone explain this to me?

---

### Post by lensman3 on 2009-07-17
Is it EXPORTed?

EXPORT LB....=<where ever>

---

### Post by rbpember on 2009-07-17
I'm running csh, so export isn't available. In any case, all the other environment variables in my interactive environment are being passed to the environment set up by "at". LD_LIBRARY_PATH seems to be singled out for some reason.

---

### Post by movieman on 2009-07-17
> **rbpember said:**
> I'm running csh, so export isn't available. In any case, all the other environment variables in my interactive environment are being passed to the environment set up by "at". LD_LIBRARY_PATH seems to be singled out for some reason.

Note: "commands will be executed using /bin/sh" so you probably need to set it in the sh profile.

Note also the man page for at (OK, I checked the CentOS version rather than Ubuntu, but I presume it's the same): "If the user submitting the at job is not the  super-user,  variables  that  alter the behaviour of the loader ld.so( 8 ), such as LD_LIBRARY_PATH, cannot be recorded and restored by at."

---

### Post by rbpember on 2009-07-17
> **movieman said:**
> Note: "commands will be executed using /bin/sh" so you probably need to set it in the sh profile.

Note also the man page for at (OK, I checked the CentOS version rather than Ubuntu, but I presume it's the same): "If the user submitting the at job is not the  super-user,  variables  that  alter the behaviour of the loader ld.so( 8 ), such as LD_LIBRARY_PATH, cannot be recorded and restored by at."

csh wasn't the issue. Every other variable in my csh environment was being recorded by at. LD_LIBRARY_PATH was the only missing one.

Your quote from the man page from CentOS is the explanation I was after. The Ubuntu man page has no explanation at all. I guess I had never thought of specifying LD_LIBRARY_PATH as modifying the loader, but, yeah, of course it does. I can see how allowing the loader to be modified in a job launched by at could be a problem.

Thanks for the explanation.

---

