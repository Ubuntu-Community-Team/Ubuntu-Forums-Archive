---
title: "Xtremely Evil Linux Virus/Trojan?"
date: 2009-12-13
forum: Security
---

### Post by njiii on 2009-12-13
In linux binaries, in any linux distro, I've discovered the same strings which I believe may be due to a virus or trojan. Yet, clamav, rkhunter, chkrootkit do not detect abnormalities. Whether I run 'strings' on the binary files or view with vim or gedit, here is what is always seen inside the binaries:

  __gmon_start__ 

 _Jv_RegisterClasses

  Followed by commands which differ within each binary. If, by some luck, I've downloaded a fresh Linux ISO where binaries do not include the above two strings followed by commands, after I run an update the updated binaries suddenly contain the above two strings and other, what I believe to be, rogue strings. I've avoided the possible infection with an OpenBSD install, yet all the Linux installations and burned ISOs contain binaries with the above two strings followed by commands. Google results are vague, some suggest shell backdoors, any help? In a few hours I've found info about people making scripts to detect malware in their binaries which includes detection of the gmonstart string and the jv registerclasses. The commands following the gmonstart string and jv registerclasses within the binaries do not appear normal in context of the files they're found in, and some repetition of gnu/dist strings along with gibberish could be thought of, as suggested by some, as keys used for shells.  **[COLOR=red]May I please have a few of you kind friends look into some of your binaries with an editor and search for these strings and post any positive results here?[/COLOR]**

 I'm not expecting anyone to do research for me, but I would enjoy it if anyone does see these stringa within some of their Linux binaries, too. On my Linux liveCDs the strings occur in a small selection of binaries, usually binaries most important/frequently used (ps, top, sshd, whois and so forth), while Linux distributions installed to HDDs and regularly updated via live internet connections have a larger portion of the binaries &quot;infected&quot; with these strings.  If the ocurrance of these strings in binaries is common or common enough, I may rest easy.  Please, humor me and look inside some of your binaries for these strings, in mine they occur towards the beginning of each &quot;infected&quot; binary. If I'm alone on this forum with such experts in finding so many of these &quot;infections&quot; across Linux distributions, it +is+ cause for concern.

 If, however, these string entries are so common and many of you discover them in several of your files, fine and I would rest easy.  If this is a new trojan or virus, it spreads quickly throughout binaries and infects everything, I haven't managed to get rid of it, only my OpenBSD box remains free of these strings.

---

### Post by unspawn on 2009-12-13
> **njiii said:**
> If, however, these string entries are so common (..) I would rest easy.
Rest easy. Common stuff:
__gmon_start__ is for use by gmon profiling (gprof),
The (weak) Jv_RegisterClasses symbol is for Java.

---

### Post by KIAaze on 2009-12-13
```
$ grep _Jv_RegisterClasses /bin/cp
Binary file /bin/cp matches
$ grep __gmon_start__  /bin/cp
Binary file /bin/cp matches

```

Then why does the copy command contain java code?

And why have such "release" binaries been compiled with profiling flags (-pg?) ? Doesn't it slow them down?

---

### Post by unspawn on 2009-12-13
> **KIAaze said:**
> why does the copy command contain java code?
It doesn't. It gets linked in on the fly and only when necessary.


> **KIAaze said:**
> why have such "release" binaries been compiled with profiling flags (-pg?)
As far as I know they haven't been. Sort of same thing as above (except that here __gmon_start__ just exists to provide call_gmon_start() with an address or something) but then again you can easily find out for yourself by looking at the source package build flags.

---

### Post by __p1n__ on 2009-12-13
> **njiii said:**
> ... I've discovered the same strings which I believe may be due to a virus or trojan...

Aha! A security hole!

> **njiii said:**
> 
 ... Yet, clamav, rkhunter, chkrootkit do not detect abnormalities.  ...

The authors of these tools don't agree. Better file a security advisory pronto. ;)

> **KIAaze said:**
> 
Then why does the copy command contain java code?


It doesn't.  It contains some default symbols that the GCC compiler put in.  If you actually compile some code and scan the symbol table in the executable then you'll see that they're tagged as weak symbols and also undefined (missing text/data address.)  There are other considerations (primarily relating to default shared objects) but that's the gist of it.

```

$ nm a.out
08049f20 d _DYNAMIC       
08049ff4 d _GLOBAL_OFFSET_TABLE_
080484dc R _IO_stdin_used       
         w _Jv_RegisterClasses  
08049f10 d __CTOR_END__         
08049f0c d __CTOR_LIST__        
08049f18 D __DTOR_END__         
08049f14 d __DTOR_LIST__        
080484ec r __FRAME_END__        
08049f1c d __JCR_END__          
08049f1c d __JCR_LIST__         
0804a018 A __bss_start          
0804a010 D __data_start         
08048490 t __do_global_ctors_aux
08048370 t __do_global_dtors_aux
0804a014 D __dso_handle         
         w __gmon_start__       
0804848a T __i686.get_pc_thunk.bx
08049f0c d __init_array_end      
08049f0c d __init_array_start    
08048420 T __libc_csu_fini       
08048430 T __libc_csu_init       
         U __libc_start_main@@GLIBC_2.0
0804a018 A _edata
0804a020 A _end
080484bc T _fini
080484d8 R _fp_hw
080482b8 T _init
08048340 T _start
0804a018 b completed.6625
0804a010 W data_start
0804a01c b dtor_idx.6627
         U exit@@GLIBC_2.0
080483d0 t frame_dummy
080483f4 T main
         U puts@@GLIBC_2.0

```

---

