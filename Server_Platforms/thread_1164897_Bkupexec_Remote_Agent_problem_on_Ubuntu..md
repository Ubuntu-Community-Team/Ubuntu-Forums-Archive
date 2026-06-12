---
title: "Bkupexec Remote Agent problem on Ubuntu."
date: 2009-05-20
forum: Server Platforms
---

### Post by wolfteeth on 2009-05-20
My environment: Windows server 2003 + Ubuntu 9.04

BackupExec 12d installed on W2003 as media server that I want to backup the Ubuntu,

since no support by Symantec, I got assistance from this post: [http://ubuntuforums.org/showthread.php?t=186128](http://ubuntuforums.org/showthread.php?t=186128) and get the Remote agent installed successfully and ensure the service is started.

I sure that the Media server (windows2003) is no problem to access the Ubuntu via Samba. However, when I setup backup job on the Media server, I could see my Linux server name under Favorite Resources -> Linux/Unix Servers, but when I explorer it, a error prompts: &#8220;An error was encountered while attempting to browser the contents of Ubuntu.. &#8221;

**I would like to know how can I setup the permission or what else that allow me to browser the Ubuntu server for backup**, below pic is one figure from symantec. [http://seer.entsupport.symantec.com/docs/282164.htm](http://seer.entsupport.symantec.com/docs/282164.htm) 

[IMG]http://seer.entsupport.symantec.com/docs/images/282164/untitled.jpg[/IMG]

---

### Post by tabascoterrier on 2009-05-20
My best guess would be an agent configuration or permissions problem.

Do you get any useful entries in /var/VRTSralus/beremote.service.log ?

Failing that, try running the daemon with console logging enabled by:
```
/opt/VRTSralus/bin/beremote --log-console
```

Hopefully the output should shed some light on your problem.

---

### Post by dbdavidson on 2009-05-20
wolfteeth,

The "how I did it" story in the thread you cited is, I'm afraid, not possible with your setup.  I was using the legacy RALUS agent that is not supported by BE 12d (support was halted midway though v11).

The "solution" is rather absurd.  Symantec is happy to sell you the current RALUS agent, which isn't cheap, but they don't offer formal support.  Additionally, the agent is only "compatible" with certain flavors of Linux and Ubuntu isn't one of them.  A Google search does offer workarounds and people have seen success with a RALUS-Ubuntu combination.

We discovered this the hard way when we upgraded to 12d without thinking first.  We were playing with the idea of mounting the desired data on a Windows server (via Samba) and backing it up that way.  Given your success with that piece you might try it.

Good luck.

---

### Post by wolfteeth on 2009-05-20
I used beremote --log-file ralusdebug export the logs for your reference:

b6448b40 Thu May 21 11:24:23 2009 : Starting BE Remote Agent
b6448b40 Thu May 21 11:24:23 2009 : Log file: ralusdebug
b6448b40 Thu May 21 11:24:23 2009 : No configuration file specified. Using default.
b6448b40 Thu May 21 11:24:23 2009 : Log to console: disabled
b6448b40 Thu May 21 11:24:23 2009 : Successfully set the supplementary groups of the process
b6448b40 Thu May 21 11:24:23 2009 : Initialized locks for SSL callbacks
b6448b40 Thu May 21 11:24:23 2009 : Starting NDMP processor
b642cb90 Thu May 21 11:24:23 2009 : FS_InitFileSys
b642cb90 Thu May 21 11:24:23 2009 : libbedsnt5.so could not be loaded: 0x 2 (2)
b642cb90 Thu May 21 11:24:23 2009 : libbedssql2.so could not be loaded: 0x 2 (2)
b642cb90 Thu May 21 11:24:23 2009 : libbedsxchg.so could not be loaded: 0x 2 (2)
b642cb90 Thu May 21 11:24:23 2009 : libbedsxese.so could not be loaded: 0x 2 (2)
b642cb90 Thu May 21 11:24:23 2009 : libbedsmbox.so could not be loaded: 0x 2 (2)
b642cb90 Thu May 21 11:24:23 2009 : libbedspush.so could not be loaded: 0x 2 (2)
b642cb90 Thu May 21 11:24:23 2009 : libbedsnote.so could not be loaded: 0x 2 (2)
b642cb90 Thu May 21 11:24:23 2009 : libbedsmdoc.so could not be loaded: 0x 2 (2)
b642cb90 Thu May 21 11:24:23 2009 : libbedssps2.so could not be loaded: 0x 2 (2)
b642cb90 Thu May 21 11:24:23 2009 : libbedssps3.so could not be loaded: 0x 2 (2)
b642cb90 Thu May 21 11:24:23 2009 : libbedsupfs.so could not be loaded: 0x 2 (2)
b642cb90 Thu May 21 11:24:23 2009 : libbedsshadow.so could not be loaded: 0x 2 (2)
b642cb90 Thu May 21 11:24:23 2009 : libbedsoffhost.so could not be loaded: 0x 2 (2)
b642cb90 Thu May 21 11:24:23 2009 : loaded libbedsvx.so
b642cb90 Thu May 21 11:24:23 2009 : loaded libbedsrman.so
b642cb90 Thu May 21 11:24:23 2009 : loaded libbedssms.so
b642cb90 Thu May 21 11:24:23 2009 : loaded libbedssmsp.so
b642cb90 Thu May 21 11:24:23 2009 : libbedsra.so could not be loaded: 0x 2 (2)
b642cb90 Thu May 21 11:24:23 2009 : libbedsdb2.so could not be loaded: 0x 2 (2)
b642cb90 Thu May 21 11:24:23 2009 : loaded libbedsedir.so
b642cb90 Thu May 21 11:24:23 2009 : libbedsvmesx.so could not be loaded: 0x 2 (2)
b642cb90 Thu May 21 11:24:23 2009 : Initializing FSs
b642cb90 Thu May 21 11:24:23 2009 : FS 1 failed to initialize: 0xE000FE46
b642cb90 Thu May 21 11:24:23 2009 : Function called: RMAN_InitFileSys
b642cb90 Thu May 21 11:24:23 2009 : Using 'UTF-8' Encoding.
b642cb90 Thu May 21 11:24:23 2009 : Using vfm path /opt/VRTSralus/VRTSvxms from config.
b642cb90 Thu May 21 11:24:23 2009 : Sucessfully set VFM_PRIVATE_ROOT env to /opt/VRTSralus/VRTSvxms.
b642cb90 Thu May 21 11:24:23 2009 : VFM_PRIVATE_ROOT was set with value /opt/VRTSralus/VRTSvxms
b642cb90 Thu May 21 11:24:23 2009 : VXMS Initialization OK.
b642cb90 Thu May 21 11:24:23 2009 : Detected Mounted Filesystem: type <ext3> mounted at </>
b642cb90 Thu May 21 11:24:23 2009 : Detected Mounted Filesystem: type <tmpfs> mounted at </lib/init/rw>
b642cb90 Thu May 21 11:24:23 2009 : Detected Mounted Filesystem: type <proc> mounted at </proc>
b642cb90 Thu May 21 11:24:23 2009 : Detected Mounted Filesystem: type <sysfs> mounted at </sys>
b642cb90 Thu May 21 11:24:23 2009 : Detected Mounted Filesystem: type <tmpfs> mounted at </var/run>
b642cb90 Thu May 21 11:24:23 2009 : Detected Mounted Filesystem: type <tmpfs> mounted at </var/lock>
b642cb90 Thu May 21 11:24:23 2009 : Detected Mounted Filesystem: type <tmpfs> mounted at </dev>
b642cb90 Thu May 21 11:24:23 2009 : Detected Mounted Filesystem: type <tmpfs> mounted at </dev/shm>
b642cb90 Thu May 21 11:24:23 2009 : Detected Mounted Filesystem: type <devpts> mounted at </dev/pts>
b642cb90 Thu May 21 11:24:23 2009 : Detected Mounted Filesystem: type <fusectl> mounted at </sys/fs/fuse/connections>
b642cb90 Thu May 21 11:24:23 2009 : Detected Mounted Filesystem: type <securityfs> mounted at </sys/kernel/security>
b642cb90 Thu May 21 11:24:23 2009 : Detected Mounted Filesystem: type <binfmt_misc> mounted at </proc/sys/fs/binfmt_misc>
b642cb90 Thu May 21 11:24:23 2009 : Detected Mounted Filesystem: type <fuse.gvfs-fuse-daemon> mounted at </home/administrator/.gvfs>
b642cb90 Thu May 21 11:24:23 2009 : Detected Mounted Filesystem: type <iso9660> mounted at </media/cdrom0>
b6448b40 Thu May 21 11:24:23 2009 : NDMPDMainThreadFunc spawned: grpid=1, tid=-1237136496
b642cb90 Thu May 21 11:24:24 2009 : Could not resolve the "bews-ndmp" or the "ndmp" service, error code: -8, using port 10000
b642cb90 Thu May 21 11:24:24 2009 : BETCPListener successfully installed a signal handler for SIGTERM
b642cb90 Thu May 21 11:24:24 2009 : BETCPListener::BETCPListener: This system appears to be a Dual IP system
b642cb90 Thu May 21 11:24:24 2009 : BETCPListener::BETCPListener: Successfully set the IPV6_V6ONLY option, this listener may behave as Dual Stack listener
b642cb90 Thu May 21 11:24:24 2009 : Started NDMP Listener on port 10000
b52e8b90 Thu May 21 11:24:34 2009 : NrdsAdvertiserThread: advertisement cycle started.
b52e8b90 Thu May 21 11:24:34 2009 : RMAN_EnumSelfDLE: AgentConfig GetOracleDBNames returned error. If Oracle Agent is installed, please run AgentConfig.
b52e8b90 Thu May 21 11:24:34 2009 : NrdsAdvertiserThread: EnumSelfDLE for file system 14 returned 0(0x0) and 0 DLEs
b52e8b90 Thu May 21 11:24:34 2009 : BENetConfigEx: Successfully refreshed adapter information.
b52e8b90 Thu May 21 11:24:34 2009 : NrdsAdvertiserThread: EnumSelfDLE for file system 22 returned 0(0x0) and 1 DLEs
b52e8b90 Thu May 21 11:24:34 2009 : NrdsAdvertiserThread: Nrds Message Len : 141.
b52e8b90 Thu May 21 11:24:34 2009 : VX_RemoveDLE: DestroyDLE()
b52e8b90 Thu May 21 11:24:34 2009 : This instance of BETCPListener was not requested to install a signal handler and hence will not install one!
b52e8b90 Thu May 21 11:24:34 2009 : ConnectToServerEndPoint: dest=192.168.0.221, service=6101
b52e8b90 Thu May 21 11:24:34 2009 : CreateConnection type=0 on socket 7 via BESocket OK
b52e8b90 Thu May 21 11:24:34 2009 : NrdsAdvertiserThread: send of Bubuntu type 22 subtype 0 to target=192.168.0.221 port=6101 succeeded
b52e8b90 Thu May 21 11:24:34 2009 : NrdsAdvertiserThread: advertisement cycle complete. Waiting 240 minutes before advertising again.
b4ae7b90 Thu May 21 11:24:39 2009 : NrdsAdvertiserThread: negative (purge) advertisement cycle started.
b4ae7b90 Thu May 21 11:24:39 2009 : NrdsAdvertiserThread: no purge is pending.
b4ae7b90 Thu May 21 11:24:39 2009 : NrdsAdvertiserThread: negative (purge) advertisement cycle complete. Waiting 240 minutes before advertising again.
b642cb90 Thu May 21 11:25:12 2009 : Control connection accepted : connection established between end-points 192.168.0.152:10000 and 192.168.0.230:1049
b42e6b90 Thu May 21 11:25:14 2009 : ndmp_readit: Caught message on closed connection. Socket 0x7 len 0x0
b42e6b90 Thu May 21 11:25:14 2009 : ndmp_readit: ErrorCode :: 0 :
b42e6b90 Thu May 21 11:25:14 2009 : FreeFormatEnv( cur_fmt=0 )
b42e6b90 Thu May 21 11:25:14 2009 : FreeFormatEnv( cur_fmt=0 )
b6448b40 Thu May 21 11:27:21 2009 : Stopping remote agent due to receipt of 'SIGTERM'
b6448b40 Thu May 21 11:27:21 2009 : Remote agent exiting, cancelling 4 joinable threads
b642cb90 Thu May 21 11:27:21 2009 : Detected a SIGTERM delivered to the process! Quitting the listener ...
b642cb90 Thu May 21 11:27:21 2009 : ndmpRun: exiting
b4ae7b90 Thu May 21 11:27:24 2009 : time to exit thread
b5ae9b90 Thu May 21 11:27:24 2009 : time to exit thread
b52e8b90 Thu May 21 11:27:24 2009 : time to exit thread

---

### Post by jonoinsa on 2010-07-08
hi wolfteeth:

found the solution to this today when I was looking.

The agent seems to have a problem with the gnome filesystem,

I did a:

umount /home/user/.gvfs

After this I could see the files system on backup exec.

Not sure what implications this has on unmounting this but have not had any problems so far.

HTH

---

### Post by Audiosears on 2011-11-10
Jon,

If you run BE jobs from shares on your Ubuntu box, it's a good idea to also have it ignore the .gvfs files if you're backing up any of the home directories - I used to get errors previously.  You'll still get other files, these just don't copy, and the only real issue is you'll have 'failures' instead of 'successes' in your logs, but no reason it can't be clean :)

Wolf - not sure @ BE 12, but I was running 8.10 at the time we first got BE 12.5 and the agent worked ok for me at that time, textbook install.  However, the RALUS agent was a bit sketchy until I installed the 5 hotfixes I needed, which admittedly weren't too simple to find.  Also, with the 12.5 hotfixes, you actually need to replace 'Debian' with 'Ubuntu' when it checks your OS version in the patch code or the patches won't install.  Symantec wasn't supporting Ubuntu at the time (Only Debian 4/5), though architecturally they're the same animal.

I'd say you'd probably want to update your Ubuntu install when you get a chance, BUT one thing I did run into was that 11.10 uses the newer 3.x Linux Kernel (whereas 11.04 and before used the 2.6.xx ones).  the RALUS agent will not work if you're running with a 3.x Kernel, but It'll install OK.  If you do update to 11.10 and reinstall the RALUS agent, make sure you restart, enter GRUB and boot with whatever your latest 2.6.x kernel is, then you'll be OK.

---

