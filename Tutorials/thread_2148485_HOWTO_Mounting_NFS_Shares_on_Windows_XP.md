---
title: "HOWTO: Mounting NFS Shares on Windows XP"
date: 2013-05-25
forum: Tutorials
---

### Post by sdgiffin on 2013-05-25
On my home LAN I have a mixed cadre of systems with XP running alongside Ubuntu, and I have movies, financial documents, printers, photos, MP3s, etc that need to be available to multiple users on both Ubuntu and Windows. Many people will say "Use SAMBA!" or "Use both!" for sharing, but I like NFS because I had many issues with SAMBA I wasn't able to resolve. So, I went to NFS. That was easy enough on the Ubuntu machines, but the XP machines were a different story. Out of the box, Microsoft's Windows XP doesn't come equipped to talk to NFS servers, which was a minor problem, but one easily fixed by downloading and installing Windows Services For Unix. For the most part, I was able to follow the guide here with regard to setting up and configuring WSFU:

[http://ubuntuforums.org/showthread.php?t=310168](http://ubuntuforums.org/showthread.php?t=310168)

It's a well written guide, and everything ran exactly as expected until I was trying to mount the Ubuntu shares on my one XP machine, failing with the error "Cannot find network" or "No network found". Naturally, I did all the standard XP Network troubleshooting steps first (check the firewall settings, etc), all of which failed to resolve the issue. Finally, I managed to resolve this by following the information below, which I discovered after exhaustive Googling:

[http://blogs.msdn.com/sfu/archive/2007/06/05/network-error-53-the-data-area-passed-to-a-system-call-is-too-small-or-unknown-error.aspx](http://blogs.msdn.com/sfu/archive/2007/06/05/network-error-53-the-data-area-passed-to-a-system-call-is-too-small-or-unknown-error.aspx)

Specifically, I changed the registry setting to use reserved ports and suddenly I was able to connect successfully:


[LIST]
[*]Open [FONT=courier new]regedit[/FONT] 
[*]Navigate to [FONT=courier new]HKLM\Software\Microsoft\Client for NFS\CurrentVersion\Default[/FONT] 
[*]Add [FONT=courier new]UseReservedPorts[/FONT] as a [FONT=courier new]DWORD[/FONT] and set it's value to [FONT=courier new]1[/FONT] 
[/LIST]

Alternatively, if you don't want to dig through the registry, you can copy the text below, save it as a [FONT=courier new].REG[/FONT] file and doubleclick in Windows:

```
Windows Registry Editor Version 5.00 
 
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Client for NFS\CurrentVersion\Default] 
"UseReservedPorts"=dword:00000001
```

After I restarted the Client for NFS service (to allow the change to take effect), I went back to Explorer, opened the "Map Network Drive" dialogue and put in the address of one of the Ubuntu shares ([FONT=courier new]192.168.2.5:/export/mp3s[/FONT] - formatted exactly like mounting them on another Ubuntu machine), Windows asked me to confirm my credentials, and I was able to mount the shares (FINALLY!), and copy files back and forth with ease. Obviously, your shares probably won't look the same, and you may not even have the same trouble. As far as I know, this should work on any non-server version of Windows from 2000 Pro up to Windows 8, but I have only tested on Windows XP.

---

### Post by sdgiffin on 2013-05-26
I should add, as an after-thought, though I should hope it goes without saying, that you should be careful when you set up your shares. Windows users may inadvertently delete dot files (like [FONT=courier new].profile[/FONT] for example), so you need to manage their permissions carefully if you are mapping a user's home directory across multiple platforms. The guide I listed above suggests mapping the Windows [FONT=courier new]Administrators[/FONT] group to the Linux [FONT=courier new]users[/FONT] group, and this is a good start, but may prevent the users from deleting files they actually intend to delete, like old copies of existing documents (spreadsheets, etc). Generally speaking however, as long as the Windows User is mapped to the correct Linux user ([FONT=courier new]John[/FONT] to [FONT=courier new]john[/FONT]), there shouldn't be any issues long term as most of the issues I've dealt with revolve around file permission conflicts.

---

