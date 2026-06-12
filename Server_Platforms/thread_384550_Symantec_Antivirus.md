---
title: "Symantec Antivirus"
date: 2007-03-14
forum: Server Platforms
---

### Post by Strelock on 2007-03-14
Did anybody managed to have it running under ubuntu?

I have all packages installed with alien now GUI runs the only problem is the scanning module itself ;)

Here is what I get:

./rtvscand: error while loading shared libraries: libecomlodrlin.so: cannot open shared object file: No such file or directory

Googled, searched without any luck....

---

### Post by markofealing on 2007-03-14
Use AVG for Linux, it's free and works!

---

### Post by Strelock on 2007-03-14
> **markofealing said:**
> Use AVG for Linux, it's free and works!

Well, I would but the corporate standards say we should use Symantec... Any suggestions anybody?

---

### Post by Adam_GUI on 2007-03-14
Only solutions I could think up are to google for the missing *.so file, or check the installation media for the missing file.

Have you checked with Symantec regarding the missing file?  If you're under contract, they should be more than happy to help you.

---

### Post by shawnlower on 2007-09-20
First off (disclaimer) as stated in the documentation, SAV for Linux's realtime virus scanning engine works *only* on supported kernels (don't get me started on this). For the command line and scheduled scanning, they only support RedHat, SuSE, and VMware ESX. Now, onto breaking the rules. I've just started working on this issue myself, and have found a few things: 

0) Of course, you'll need to use alien to convert the RPMs into debs. (alien -cv *.rpm)

1) the libecomlodrlin.so errors can be fixed pretty easily. The files are under /opt/Symantec/symantec_antivirus (or whichever root directory you chose) I just symlinked them into /usr/lib and did away with those errors

2) Symantec has hardcoded the path to awk into the scripts (/bin/awk). On Ubuntu, it should be /usr/bin. I fixed that in the /etc/init.d/symcfgd and rtvscand startup scripts.

3) It tries to touch the /var/lock/subsys/symcfgd file. Ubuntu doesn't contain the /var/lock/subsys directory, and the installer doesn't create it. You'll need to.

4) In my case, no default configuration file was created. Running ./symcfgpop ./symcfgdata.inf from the /opt/Symantec/symantec_antivirus directory seemed to create the default set of configuration settings. They could then be viewed by running ./symcfg -r list

After this was done, manual scanning worked! 
./sav manualscan -s /lib
./sav info -s 
General Status: Scanning files
Manual Scan Status: Scanning files

5) /opt/Symantec/symantec_antivirus/rtvscand exits immediately after starting it. Likely due to the kernel issues. Even running in foreground with debugging, and verbose logging doesn't provide any hints. I've just started a few minutes ago on this problem, and am not sure what's up with this one. I'll update if I find anything. Anyone else....

---

### Post by spinnekoppeke on 2007-11-15
Hi,

I have symantec client for  antivirus mr3, and am netwerk admin on company, and they only let me put a linux client into the network , if I update to the antivirus-database. So big problem. I tried with Fedora 8 but there he gave problems with the libraries. NOw i try with ubuntu. 
I followed your recommendations : 
1. created debs with alien
2. changing path for awk
3. creating the lock file

When I run  ./symcfgpop I receive : 
root@gandalf:/opt/Symantec/symantec_antivirus# ./symcfgpop symcfgpop: Settings popoulation utility for Symantec AntiVirus
Usage: symcfgpop <settings file to import>

When I run ../symcfgdata.inf I receive : 
./symcfgdata.inf: line 1: syntax error near unexpected token `;'
./symcfgdata.inf: line 1: `;***************************************************************************'

 ./sav manualscan -s /lib
Error: Symantec configuration service unavailable
Unable to open key \VirusProtect6
Unable to determine status of scanning daemon
 *** This command may not function correctly or may be delayed
Error: Symantec configuration service unavailable
Unable to open registry key!
Error: Symantec configuration service unavailable
Unable to create key ScanAllDrives
Error: Symantec configuration service unavailable
Unable to write value to registry!
Error: Symantec configuration service unavailable
Unable to create key /lib
Error: Symantec configuration service unavailable
Unable to write value to registry!
Error: Symantec configuration service unavailable
Unable to create key StartManualScanNow
Error: Symantec configuration service unavailable
Unable to write StartManualScanNow value to registry!


And when I do /opt/Symantec/symantec_antivirus/rtvscand
failed to open PID file: No such file or directory

When I open the gui, it says autoprotect : disabled , RTVScan : disabled, Scan : unknown status.


Anybody has ideas ?
Greetings,
Johan

---

### Post by spinnekoppeke on 2007-11-15
What I forgot to say, I had to manually create VIRSCAN8.dat, VIRSCAN9.DAT, VIRSCANT.dat, WHATSNEW.txt, ZDONE.dat, otherwise I receive the errors

chown: cannot access `/opt/Symantec/virusdefs/temp/VIRSCAN8.DAT': No such file or directory
chown: cannot access `/opt/Symantec/virusdefs/temp/VIRSCAN9.DAT': No such file or directory
chown: cannot access `/opt/Symantec/virusdefs/temp/VIRSCANT.DAT': No such file or directory
chown: cannot access `/opt/Symantec/virusdefs/temp/WHATSNEW.TXT': No such file or directory
chown: cannot access `/opt/Symantec/virusdefs/temp/ZDONE.DAT': No such file or directory

I also manually had to create the group avdefs

---

