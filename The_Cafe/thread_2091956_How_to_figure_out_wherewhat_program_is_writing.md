---
title: "How to figure out where/what program is writing"
date: 2012-12-06
forum: The Cafe
---

### Post by astef on 2012-12-06
Hi everyone,

I have a third-party program installed (binary, no source code) that keeps crashing. Support from provider is close to useless. iotop shows that the program (idle) keeps writing to disk. top also shows it uses more and more CPU until 100% when it becomes unresponsive. 

Is there a way to figure out what this program is writing? Maybe I can modify the output file somehow.

Thanks

---

### Post by drmrgd on 2012-12-06
Maybe you could run it from the terminal with a strace dump to see what it's writing and what resources are being use?  Just run strace <program_name>.  You could also add the -o option to write the output to a file for easier parsing.

---

### Post by SeijiSensei on 2012-12-06
Run lsof as root with sudo.  If you use

```
sudo lsof | grep program_name
```

you'll see all the files being used by "program_name".

---

### Post by drmrgd on 2012-12-06
> **SeijiSensei said:**
> Run lsof as root with sudo.  If you use

```
sudo lsof | grep program_name
```

you'll see all the files being used by "program_name".

Ahhh....totally didn't think of 'lsof'.  To extend on that notion (very good idea!), you can get that information in htop as well, which might in conjunction with the rest of the htop output give a little more clear picture.

---

### Post by astef on 2012-12-06
Works like a charm. Thanks!

---

