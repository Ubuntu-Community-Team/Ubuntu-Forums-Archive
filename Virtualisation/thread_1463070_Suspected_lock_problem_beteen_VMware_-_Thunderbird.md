---
title: "Suspected lock problem beteen VMware - Thunderbird"
date: 2010-04-26
forum: Virtualisation
---

### Post by jamrlm on 2010-04-26
I believe that this is a VMware and mozilla lock problem. I am running 9.10 with all updates installed.  For several years I have been unable to download and extract thunderbird into its directory and then start TB using a terminal command /.../thunderbird/thunderbird.  It always returned "thunderbird-bin no file or directory". I have verified that right before the call to thunderbird-bin in the shell that the dir is correct.  For TB2, apt-get install seemed to clear the problem.  Later on when starting Firefox out of TB, I would get the message popup that Firefox was busy and then continue on.  
   Now the installation of TB3 is driving me nuts. I get the same busy message when trying to start TB3 and it stops!! So I said OK back to TB2.  I extracted an old TB2 tar ball and did my command and lo and behold there was more to the error message.  "error while loading shared libraries: libstdc++.so.5: cannot open shared object file:No such file or directory". Some enlightened person at Mozilla had provided the real reason instead of just dumping out misleading crap.  So after several find attempts I did a "find / -name libstdc* -print" which turned up 19 lines all involving libstdc++.so.6 (No 5s), 8 with VMware involved, and 2 of those like "home/rlm/.mozilla/firefox/c0f945ih.default/extensions/VMwareVMRC@vmware.com/plugins/lib/libstdc++.so.6"
   This is why I think I have a lock file problem except that the lock file has been gone for a long time. Always the first system under vmware that I would install would be Firefox.  Some where in the distant past I might have installed Thunderbird also??
   I have had a love/hate relationship with VMware with many reinstalls so if it has to go that is OK. I can reinstall it again but absolutely without Firefox or TB.
   I am over my head on how to fix this problem.  Any help would be greatly appreciated and would allow me to move forward with TB3.  Thanks to all.

---

### Post by dcstar on 2010-05-01
> **jamrlm said:**
> I believe that this is a VMware and mozilla lock problem. I am running 9.10 with all updates installed.  For several years I have been unable to download and extract thunderbird into its directory and then start TB using a terminal command /.../thunderbird/thunderbird.  It always returned "thunderbird-bin no file or directory". I have verified that right before the call to thunderbird-bin in the shell that the dir is correct.  For TB2, apt-get install seemed to clear the problem.  Later on when starting Firefox out of TB, I would get the message popup that Firefox was busy and then continue on.  
   Now the installation of TB3 is driving me nuts. I get the same busy message when trying to start TB3 and it stops!! So I said OK back to TB2.  I extracted an old TB2 tar ball and did my command and lo and behold there was more to the error message.  "error while loading shared libraries: libstdc++.so.5: cannot open shared object file:No such file or directory". Some enlightened person at Mozilla had provided the real reason instead of just dumping out misleading crap.  So after several find attempts I did a "find / -name libstdc* -print" which turned up 19 lines all involving libstdc++.so.6 (No 5s), 8 with VMware involved, and 2 of those like "home/rlm/.mozilla/firefox/c0f945ih.default/extensions/VMwareVMRC@vmware.com/plugins/lib/libstdc++.so.6"
   This is why I think I have a lock file problem except that the lock file has been gone for a long time. Always the first system under vmware that I would install would be Firefox.  Some where in the distant past I might have installed Thunderbird also??
   I have had a love/hate relationship with VMware with many reinstalls so if it has to go that is OK. I can reinstall it again but absolutely without Firefox or TB.
   I am over my head on how to fix this problem.  Any help would be greatly appreciated and would allow me to move forward with TB3.  Thanks to all.

Let me guess, trying to manually install 32-bit apps on a 64-bit host?

---

