---
title: "mpich2 invalid port info error"
date: 2008-12-20
forum: Server Platforms
---

### Post by tom_z on 2008-12-20
Hi,

  I have installed mpich2 on two computers bp1 and bp2. It works fine individually on each computer either locally or by ssh. But when I try to run mpdboot -n 2 I got the following error:

debug: starting
running mpdallexit on bp1
debug: launch cmd= /usr/local/bin/mpd.py   --ncpus=1 -e -d
debug: mpd on bp1  on port 39944
debug: info for running mpd: {'ncpus': 1, 'list_port': 39944, 'entry_port': '', 'host': 'bp1', 'entry_host': '', 'ifhn': ''}
debug: launch cmd= ssh -x -n -q bp2 '/usr/local/bin/mpd.py  -h bioproximity1 -p 39944  --ncpus=1 -e -d'
debug: mpd on bp2  on port no_port
mpdboot_bp1 (handle_mpd_output 406): from mpd on bp2, invalid port info:
no_port


    Any help is highly appreciated. 

    Tom

---

### Post by steigers on 2009-02-25
I encountered the same problem. In my case, the following was the case:

I installed python into a nonstandard location and set the LD_LIBRARY_PATH environment variable to the directory where libPython2.5.so.1.0 was located. However, my .cshrc (or .bashrc) was configured such that this variable is not set when logging in without a prompt, which is exactly what mpdboot.py is doing. So this resulted in not being able to load the python library, and for some odd reason it gave the error no_port in the end.

Solution: Be sure to load LD_LIBRARY_PATH when mpdboot.py is ssh-ing the other machines.

---

### Post by bigbusyboy on 2009-10-18
> **steigers said:**
> I encountered the same problem. In my case, the following was the case:

I installed python into a nonstandard location and set the LD_LIBRARY_PATH environment variable to the directory where libPython2.5.so.1.0 was located. However, my .cshrc (or .bashrc) was configured such that this variable is not set when logging in without a prompt, which is exactly what mpdboot.py is doing. So this resulted in not being able to load the python library, and for some odd reason it gave the error no_port in the end.

Solution: Be sure to load LD_LIBRARY_PATH when mpdboot.py is ssh-ing the other machines.

right. if u set LD_LIBRARY_PATH in your .bashrc file, do source it:
$vi .bashrc
 LD_LIBRARY_PATH=$MPICH2_HOME/lib:$LD_LIBRARY_PATH
$source ~/.bashrc

---

