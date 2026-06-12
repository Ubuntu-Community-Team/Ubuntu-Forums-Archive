---
title: "(Impish) Chrome_IOThread issues?"
date: 2021-09-09
forum: Ubuntu Development Version
---

### Post by 3vi1 on 2021-09-09
Has anyone else started experiencing issues running Chromium-based apps in the last week or three?  I wanted to see if this is widespread before I create a Launchpad bug report.  I searched for an existing report there, but didn't see anything that looked similar.

The Symptoms:  I first noticed the problem when I tried to launch teams-insiders (Microsoft Teams beta) for the first time in a week.  It would not launch and I found the following in the dmesg output:

```
[  653.714267] traps: Chrome_IOThread[13582] trap invalid opcode ip:55e77adb8934 sp:7fe4cd0cd4d0 error:0 in teams-insiders[55e7787c2000+5fbe000]
```

Some searches turned up older similar issues where Teams would not work for others until a reboot.  So, I rebooted for the first time in 20 day.

Unfortunately, it didn't change the symptoms.  In fact, I noticed Vivaldi (also chromium-based) would no longer start either.

I launched an electron-wrapped app I had created long ago myself via nativefier... and it also failed to start.  It also leaves a Chrome_IOThread dmesg log:

```
[  382.903339] traps: Chrome_IOThread[12705] trap int3 ip:561036813664 sp:7f097ebb3490 error:0 in 8BitWorkshop[561034242000+5f85000]
```

Oddly, Chrome, Vivaldi-Snapshot, and *even the Chromium web browser* all work fine.  :\

Reinstalling teams-insiders made no difference.

I was wondering if it was another kernel 5.13 issue, so I installed the mainline 5.14.2 kernel... same issue.  I also tried rebooting into 5.11.... same issue.

code-insiders also now appears to have the same problem as Teams:

```
[ 1060.228147] traps: Chrome_IOThread[14829] trap invalid opcode ip:55b09720c653 sp:7f8cb7003200 error:0 in code-insiders[55b094a65000+5ee2000]
```

All non-chromium apps appear to work fine - even Vulkan games (using nVidia 470.63.01 drivers).  I completely removed/reinstalled the video drivers, but that's made no difference either.

Anyone else experiencing this?

Edit:  I suspect this is related to hardware acceleration - and that the chromium based browsers I have that still work simply do not have it enabled.  Perhaps a change in the newest nVidia drivers broke something?

Edit2:  Err... scratch that... looks like Chrome, which works... has hardware acceleration enabled.  :\

---

### Post by 3vi1 on 2021-09-09
Additional errors seen when running Vivaldi from the command line:

[FONT=Courier New][39791:39814:0909/100710.911661:ERROR:gpu_process_host.cc(999)] GPU process exited unexpectedly: exit_code=159
[39791:39814:0909/100711.068729:ERROR:gpu_process_host.cc(999)] GPU process exited unexpectedly: exit_code=159
[39791:39814:0909/100711.220266:ERROR:gpu_process_host.cc(999)] GPU process exited unexpectedly: exit_code=159
[39859:39859:0909/100711.241716:ERROR:gpu_init.cc(441)] Passthrough is not supported, GL is swiftshader
[39791:39814:0909/100711.305664:ERROR:gpu_process_host.cc(999)] GPU process exited unexpectedly: exit_code=159
[39863:39863:0909/100711.314066:ERROR:gpu_init.cc(441)] Passthrough is not supported, GL is swiftshader
[39791:39814:0909/100711.378426:ERROR:gpu_process_host.cc(999)] GPU process exited unexpectedly: exit_code=159
[39867:39867:0909/100711.386063:ERROR:gpu_init.cc(441)] Passthrough is not supported, GL is swiftshader
[39791:39814:0909/100711.454495:ERROR:gpu_process_host.cc(999)] GPU process exited unexpectedly: exit_code=159
[39886:39886:0909/100711.457687:ERROR:gpu_init.cc(441)] Passthrough is not supported, GL is disabled
[39791:39814:0909/100711.540639:ERROR:gpu_process_host.cc(999)] GPU process exited unexpectedly: exit_code=159
[39901:39901:0909/100711.560472:ERROR:gpu_init.cc(441)] Passthrough is not supported, GL is disabled
[39791:39791:0909/100711.615944:ERROR:vivaldi_ui_web_contents_delegate.cc(42)] UI Process abnormally terminates with status 3 after running for 0.1552
22 seconds!
[39791:39791:0909/100711.622754:ERROR:vivaldi_ui_web_contents_delegate.cc(73)] Quiting Vivaldi
[39791:39814:0909/100711.638266:ERROR:gpu_process_host.cc(999)] GPU process exited unexpectedly: exit_code=159
[39924:39924:0909/100711.646105:ERROR:gpu_init.cc(441)] Passthrough is not supported, GL is disabled
[/FONT]

---

### Post by 3vi1 on 2021-09-09
Looks like I found someone else who hit this yesterday:  [https://github.com/microsoft/vscode/issues/132609]("https://github.com/microsoft/vscode/issues/132609")

He suspects an incompatibility between systemd 249 and chrome <93 / electron <14.0 when paired with hosts using nvidia GPUs and the nVidia drivers.

**Edit:**  And it looks like he's right.  I just rebuilt my own previously failing 8bitworkshop app with electron 15 and it now works fine.

---

### Post by jeremyhcl on 2021-09-27
This thread is the first search result when searching for the reason why Teams isn't starting. In case anyone else gets here looking for a Teams fix, you need to vote up this bug at Microsoft's site: [https://microsoftteams.uservoice.com/forums/908686-bug-reports/suggestions/44118390-systemd-249-incompatibility-issue-with-apps-teams](https://microsoftteams.uservoice.com/forums/908686-bug-reports/suggestions/44118390-systemd-249-incompatibility-issue-with-apps-teams)

---

