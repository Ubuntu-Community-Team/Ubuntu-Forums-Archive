---
title: "zenmap on acer one running UNR"
date: 2009-08-12
forum: Security
---

### Post by wardolb on 2009-08-12
when i try to perform a scan on my local machine zenmap pumps this out

nitiating OS detection (try #1) against 192.168.89.11
Retrying OS detection (try #2) against 192.168.89.11
SCRIPT ENGINE: Initiating script scanning.
SCRIPT ENGINE: '/usr/share/nmap/scripts/dns-test-open-recursion.nse' threw a run time error and could not be loaded.
SCRIPT ENGINE: '/usr/share/nmap/scripts/skype_v2-version.nse' threw a run time error and could not be loaded.
SCRIPT ENGINE: error while initializing script rules:
/usr/share/nmap/scripts/script.db:20: rpcinfo.nse is not a file!
stack traceback:
	[C]: in function 'Entry'
	/usr/share/nmap/scripts/script.db:20: in main chunk
	[C]: ?
	[C]: ?

SCRIPT ENGINE: Aborting script scan.
Host 192.168.89.11 appears to be up ... good.
All 1000 scanned ports on 192.168.89.11 are closed
Too many fingerprints match this host to give specific OS details
Network Distance: 0 hops

Read data files from: /usr/share/nmap
OS and Service detection performed. Please report any incorrect results at [http://nmap.org/submit/](http://nmap.org/submit/) .
Nmap done: 1 IP address (1 host up) scanned in 2.32 seconds
           Raw packets sent: 1012 (45.668KB) | Rcvd: 2022 (86.616KB)


any advice?

---

