---
title: "The Gnome ~/.gvfs annoyance ..."
date: 2012-05-28
forum: Server Platforms
---

### Post by eriksank on 2012-05-28
I hope this is the right forum section/prefix to post this issue in. I am developing an application -- on my laptop but for server-side use -- that calls the **quotacheck** and **quotaon** command under the hood. I have run into the following serious issues. I hope anybody is interested in weighing in ;-)

**quotacheck** refuses to run, because it cannot **stat** that notorious Gnome folder: **~/.gvfs**. Since other commands such as **lsof** command do not work either when that notorious Gnome folder is around, this is really not a **quotacheck** issue. 

No problem, I thought, because then I would just go back to runlevel 1 with the command: **init 1** or **telinit 1**. Problem. Won't work. The command does not work on Ubuntu, even though it works in any other linux distribution including Debian. This looks like a real Ubuntu problem. Why does Ubuntu crash on those commands?

So, no problem, I use another workaround and I change the runlevel in **/etc/init/rc-sysinit.conf** DEFAULT_RUNLEVEL=1, and then I reboot the machine.

That won't work either, because my laptop is a **Lenovo S10-3C**. The keyboard does not work unless ubuntu executes first the **sfnet_s10-3c-keybdrv** hackatron program (which you can find here: [http://es.sourceforge.jp/projects/sfnet_s10-3c-keybdrv](http://es.sourceforge.jp/projects/sfnet_s10-3c-keybdrv)). Apparently, **/etc/rc.local** is not triggered in runlevel 1. I cannot trigger the hackatron manually either, because the keyboard will not work or accept any input before the program has been triggered.

So, the only workaround hackatron I could find, is to unmount that Gnome thing: $ **umount ~/.gvfs; chmod 755 ~/.gvfs**. It works. **quotacheck** is now finally willing to work as normal, fix the **quota.user** file, so that **quotaon** is finally willing to switch on the quota system on my laptop.

By the way, **quotacheck** only works properly in Ubuntu if I force it to use the v1 file format: $ **quotacheck --format=vfsold -um $mountPoint**. Otherwise, it starts looking for **aquota.user** instead of **quota.user**.

This is a real **quotacheck** problem. I have check the quota-tools source. If the function **v1_check_file** in **quotaio_v1.c** finds an empty **quota.user** file or finds a file for which the size is not in multiples of exactly 40 bytes (sizeof(struct v1_disk_dqblk)), it will fail. This will trigger the quota tools to ignore the v1 mount option (**usrquota**), which clearly indicates v1 and not v2, and to start looking anyway for a v2 quota file, that is **aquota.user** instead of **quota.user**.

In my opinion the bug is caused by the way quota-tools source code intermixes v1 (quota.user) and v2 (aquota.user) related code, and the way it suddenly defaults to v2 for no good reason at all. The quota-tools are bound to fail in a tremendously large number of use cases where people try to mount a v1 quota filesystem and get error messages about missing v2 quota files.

Concerning **~/.gvfs**, is there a proper way to permanently remove or neutralize that horrible Gnome folder **~/.gvfs**?

Apparently, it is mainly used to let Nautilus mount remote filesystems virtually, for example, over SFTP. However, that SFTP facility is so incredibly buggy in Nautilus that I have switched to Filezilla long ago. As soon as Nautilus loses its connection to a remote SFTP share, it will never manage to mount it properly again. This happens frequently when using a wireless 3G connection, which can become unreliable, even if it just starts raining in the neighbourhood. In that case, only rebooting helps. So, Nautilus/SFTP is simply unusable.

I seem to be paying the price for something I really do not want to use anyway. Is there any way to get rid of that **~/.gvfs** Gnome thing, short of getting rid of Gnome altogether? I see that Ubunty's unity system builds on top of Gnome, while I would like to keep Unity.

I pretty much standardized on laptops and servers on Ubuntu and I don't want to change distribution, and move over to Arch or Debian or something similar, just to get rid of that **~/.gvfs** folder.

Any solution?

---

