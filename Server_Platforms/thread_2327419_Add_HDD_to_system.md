---
title: "Add HDD to system"
date: 2016-06-10
forum: Server Platforms
---

### Post by Sxcd1 on 2016-06-10
I have 3 HDD in my computer
HDD 1 which as 2 partitions with Windows 7 on each
HDD 2 has Ubuntu Server on large drive
HDD 3 has Ubuntu Server on small drive
1) When booting into HDD2 in Ubuntu can I get access to data on HDD3? How do you do that from the CLI?
2) Can I access data on another windows computer on the network?

---

### Post by DuckHook on 2016-06-10
> **Sxcd1 said:**
> 1) When booting into HDD2 in Ubuntu can I get access to data on HDD3?Yes, provided that you have permissions set to allow access. If you log in with the same username in both installations, then this should be no problem. As with all HDDs in Linux, you must first mount the disk before you can access it.> How do you do that from the CLI?Following are instructions for mounting/unmounting disks from the command line: [https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)

Note, you can even mount/unmount your Windows data as per instructions in this Wiki:[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)
> 2) Can I access data on another windows computer on the network?Yes. You will need to turn on file sharing on your Windows computers, but after that, accessing data from the Ubuntu side is pretty transparent. Follow only the "Client Access" instructions from this Wiki: [https://help.ubuntu.com/community/Samba/SambaClientGuide](https://help.ubuntu.com/community/Samba/SambaClientGuide)

---

### Post by Sxcd1 on 2016-06-11
I got the drive mounted but I want to access it with a samba share on my window 10 machine.
```
smbclient -L //192.168.1.5/var/windows/ -U <myusername>
```
```
WARNING: The "syslog" option is deprecated
Enter <myusername> password: 
Domain=[WORKGROUP] OS=[Windows 6.1] Server=[Samba 4.3.9-Ubuntu]
```


    ```
Sharename       Type      Comment
    ---------       ----      -------
    print$          Disk      Printer Drivers
    <folder_name>   Disk      
    IPC$            IPC       IPC Service (n1G server (Samba, Ubuntu))
Domain=[WORKGROUP] OS=[Windows 6.1] Server=[Samba 4.3.9-Ubuntu]




    Server               Comment
    ---------            -------
    N1G              n1G server (Samba, Ubuntu)


    Workgroup            Master
    ---------            -------
    WORKGROUP            N1G
```
```
smbclient //192.168.1.5/var/windows/ -U <myusername>
```
I get 
```
Domain=[WORKGROUP] OS=[Windows 6.1] Server=[Samba 4.3.9-Ubuntu]tree connect failed: NT_STATUS_BAD_NETWORK_NAME



```

---

### Post by DuckHook on 2016-06-11
> **Sxcd1 said:**
> ...Can I access data on another windows computer on the network?Based on my interpretation of your original post, I took this to mean that you wanted your Linux box to be able to read data that is residing on a windows host. But based on your subsequent actions and questions, I am wondering if what you want to do is for Windows computers to access data on your Linux box? In other words, do you want to turn your Linux box into a server?

If so, then the instructions you are following won't work. Those instructions are for setting your Ubuntu box up as a *client*, not a *server*.

Firstly, full disclosure. I haven't used *Samba* in years because I no longer have any Windows machines around. So my knowledge is very limited on this one. However, it is routinely done and the instructions are in the following Wiki pages:

[https://help.ubuntu.com/lts/serverguide/samba-fileserver.html](https://help.ubuntu.com/lts/serverguide/samba-fileserver.html)
A briefer wiki is [here]("https://help.ubuntu.com/community/How%20to%20Create%20a%20Network%20Share%20Via%20Samba%20Via%20CLI%20(Command-line%20interface/Linux%20Terminal)%20-%20Uncomplicated,%20Simple%20and%20Brief%20Way!").

Setting up a Samba server is a more involved process than setting up a client, but Samba is one of the most common tasks that Linux-based servers are used for.

I am also taking the liberty of moving this thread to the *Server Platforms* subforum where better minds than mine can help you. If my assumptions are wrong, just report this post and one of the staff will move the thread back into *New to Ubuntu* for you.

---

