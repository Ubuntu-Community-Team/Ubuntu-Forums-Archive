---
title: "CDE: automatic packaging of Code, Data, and Environment"
date: 2010-11-14
forum: The Cafe
---

### Post by andlinux on 2010-11-14
I found this today on the web and it's maybe something for the Ubuntu community.

Source: [http://stanford.edu/~pgbovine/cde.html](http://stanford.edu/~pgbovine/cde.html)

CDE is a tool that automatically packages up the Code, Data, and Environment involved in running any set of Linux commands so that they can execute identically on another computer without any installation or configuration. The only requirement is that the other computer have the same hardware architecture (e.g., x86) and major kernel version (e.g., 2.6.X) as yours. CDE allows you to easily run programs without the dependency hell that inevitably occurs when attempting to install software or libraries. You can use CDE to allow your colleagues to reproduce and build upon your computational experiments, to quickly deploy prototype software to a compute cluster, and to submit executable bug reports.

CDE is easy to use: Simply prepend any Linux command (or series of commands) with cde, and CDE will execute that command, monitor its actions, and automatically copy all files it accesses (e.g., executables, dynamically linked/loaded libraries, plug-ins, scripts, configuration/data files) into a package within your current working directory. Now you can transfer the package to another computer and run that same command without installing anything. In short, if you can run a set of Linux commands on your computer, then CDE enables others to run it on theirs.

CDE is strictly more powerful than static linking and binary packaging tools, since it can collect run-time dependencies (e.g., configuration files) that programs often require. Also, CDE can monitor commands that consist of multiple program invocations: For example, if you use it to monitor a run of a shell script or make to compile source code, CDE will package up all executables and auxiliary files (e.g., compiler, linker, assembler, headers) necessary to re-run that entire compilation process end-to-end on another computer.

Video: [http://vimeo.com/16684443]("http://vimeo.com/16684443")

---

### Post by Spice Weasel on 2010-11-14
CDE will always mean Common Desktop Environment to me.

---

### Post by llelectronics on 2010-11-14
So basically this projects takes a snapshot of the libraries that an app needs during runtime and will package this together with an fakeroot kind of directory and executable. Hmm... seems to me like a OSXish .app Directory .

---

