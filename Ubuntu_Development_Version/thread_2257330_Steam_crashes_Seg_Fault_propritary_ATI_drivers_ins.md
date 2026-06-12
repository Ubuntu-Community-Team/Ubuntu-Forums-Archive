---
title: "Steam crashes Seg Fault propritary ATI drivers installed otherwise fresh install"
date: 2014-12-19
forum: Ubuntu Development Version
---

### Post by darksidedude on 2014-12-19
hey all. just installed 15.04 Kubuntu, fully updated tried to install steam so I can get my game on =)

anyhow It crashes with a seg fault here is the konsole output and crash log 

```
jspooner@jspooner-HP-ENVY-dv6-Notebook-PC:~$ steam
Running Steam on ubuntu 15.04 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(0_client)
Uploading dump (out-of-process) [proxy '']
/tmp/dumps/crash_20141218225131_1.dmp
Finished uploading minidump (out-of-process): success = no
error: libcurl.so: cannot open shared object file: No such file or directory
/home/jspooner/.local/share/Steam/steam.sh: line 730:  3199 Segmentation fault      (core dumped) $STEAM_DEBUGGER "$STEAMROOT/$STEAMEXEPATH" "$@"
mv: cannot stat ‘/home/jspooner/.steam/registry.vdf’: No such file or directory
Installing bootstrap /home/jspooner/.local/share/Steam/bootstrap.tar.xz
Reset complete!

```

and the crash log 

```
AuthenticAMDLinux 3.16.0-28-generic #38-Ubuntu SMP Fri Dec 12 17:37:40 UTC 2014 x86_64processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 21
model		: 16
model name	: AMD A10-4600M APU with Radeon(tm) HD Graphics
stepping	: 1
microcode	: 0x6001116
cpu MHz		: 1400.000
cache size	: 2048 KB
physical id	: 0
siblings	: 4
core id		: 0
cpu cores	: 2
apicid		: 16
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 popcnt aes xsave avx f16c lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 tce nodeid_msr tbm topoext perfctr_core perfctr_nb arat cpb hw_pstate npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold bmi1
bogomips	: 4591.45
TLB size	: 1536 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm 100mhzsteps hwpstate cpb eff_freq_ro

processor	: 1
vendor_id	: AuthenticAMD
cpu family	: 21
model		: 16
model name	: AMD A10-4600M APU with Radeon(tm) HD Graphics  
stepping	: 1
microcode	: 0x6001116
cpu MHz		: 2300.000
cache size	: 2048 KB
physical id	: 0
siblings	: 4
core id		: 1
cpu cores	: 2
apicid		: 17
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 popcnt aes xsave avx f16c lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 tce nodeid_msr tbm topoext perfctr_core perfctr_nb arat cpb hw_pstate npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold bmi1
bogomips	: 4591.45
TLB size	: 1536 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm 100mhzsteps hwpstate cpb eff_freq_ro

processor	: 2
vendor_id	: AuthenticAMD
cpu family	: 21
model		: 16
model name	: AMD A10-4600M APU with Radeon(tm) HD Graphics  
stepping	: 1
microcode	: 0x6001116
cpu MHz		: 1400.000
cache size	: 2048 KB
physical id	: 0
siblings	: 4
core id		: 2
cpu cores	: 2
apicid		: 18
initial apicid	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 popcnt aes xsave avx f16c lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 tce nodeid_msr tbm topoext perfctr_core perfctr_nb arat cpb hw_pstate npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold bmi1
bogomips	: 4591.45
TLB size	: 1536 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm 100mhzsteps hwpstate cpb eff_freq_ro

processor	: 3
vendor_id	: AuthenticAMD
cpu family	: 21
model		: 16
model name	: AMD A10-4600M APU with Radeon(tm) HD Graphics  
stepping	: 1
microcode	: 0x6001116
cpu MHz		: 1400.000
cache size	: 2048 KB
physical id	: 0
siblings	: 4
core id		: 3
cpu cores	: 2
apicid		: 19
initial apicid	: 3
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 popcnt aes xsave avx f16c lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 tce nodeid_msr tbm topoext perfctr_core perfctr_nb arat cpb hw_pstate npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold bmi1
bogomips	: 4591.45
TLB size	: 1536 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm 100mhzsteps hwpstate cpb eff_freq_ro

Name:	steam
State:	t (tracing stop)
Tgid:	3326
Ngid:	0
Pid:	3326
PPid:	3083
TracerPid:	3327
Uid:	1000	1000	1000	1000
Gid:	1000	1000	1000	1000
FDSize:	256
Groups:	4 24 27 30 46 114 129 1000 
VmPeak:	   54704 kB
VmSize:	   54596 kB
VmLck:	       0 kB
VmPin:	       0 kB
VmHWM:	   45380 kB
VmRSS:	   45380 kB
VmData:	    6060 kB
VmStk:	     140 kB
VmExe:	    2412 kB
VmLib:	   42664 kB
VmPTE:	     124 kB
VmSwap:	       0 kB
Threads:	1
SigQ:	1/29242
SigPnd:	0000000000000000
ShdPnd:	0000000000000000
SigBlk:	00000000000104e8
SigIgn:	0000000000002012
SigCgt:	00000001800004e8
CapInh:	0000000000000000
CapPrm:	0000000000000000
CapEff:	0000000000000000
CapBnd:	0000003fffffffff
Seccomp:	0
Cpus_allowed:	f
Cpus_allowed_list:	0-3
Mems_allowed:	00000000,00000001
Mems_allowed_list:	0
voluntary_ctxt_switches:	48
nonvoluntary_ctxt_switches:	19
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=15.04
DISTRIB_CODENAME=vivid
DISTRIB_DESCRIPTION="Ubuntu Vivid Vervet (development branch)"
/home/jspooner/.local/share/Steam/ubuntu12_32/steamXDG_VTNR=1KDE_MULTIHEAD=falseXDG_SESSION_ID=2SSH_AGENT_PID=1578QML2_IMPORT_PATH=/usr/lib/x86_64-linux-gnu/qt5/qml/TERM=xtermSHELL=/bin/bashXDG_SESSION_COOKIE=dfb37845747eddcaca11c0fc5493a668-1418967263.939626-2067202019KONSOLE_DBUS_SERVICE=:1.73GTK2_RC_FILES=/etc/gtk-2.0/gtkrc:/home/jspooner/.gtkrc-2.0:/home/jspooner/.config/gtkrc-2.0KONSOLE_PROFILE_NAME=ShellSTEAM_RUNTIME=/home/jspooner/.local/share/Steam/ubuntu12_32/steam-runtimeGTK_RC_FILES=/etc/gtk/gtkrc:/home/jspooner/.gtkrc:/home/jspooner/.config/gtkrcGS_LIB=/home/jspooner/.fontsWINDOWID=102760474OLDPWD=/home/jspooner/.local/share/SteamSHELL_SESSION_ID=0c17188911d740008a858e4aa5f31c62KDE_FULL_SESSION=trueXDG_SESSION_CLASS=userUSER=jspoonerLIBGL_DRIVERS_PATH=/usr/lib/fglrx/dri:/usr/lib/x86_64-linux-gnu/dri:/usr/lib/dri:/usr/lib32/fglrx/dri:/usr/lib/i386-linux-gnu/driLS_COLORS=rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arc=01;31:*.arj=01;31:*.taz=01;31:*.lha=01;31:*.lz4=01;31:*.lzh=01;31:*.lzma=01;31:*.tlz=01;31:*.txz=01;31:*.tzo=01;31:*.t7z=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.lrz=01;31:*.lz=01;31:*.lzo=01;31:*.xz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.war=01;31:*.ear=01;31:*.sar=01;31:*.rar=01;31:*.alz=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.cab=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.webm=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.cgm=01;35:*.emf=01;35:*.axv=01;35:*.anx=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.m4a=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:*.axa=00;36:*.oga=00;36:*.spx=00;36:*.xspf=00;36:LD_LIBRARY_PATH=/home/jspooner/.local/share/Steam/ubuntu12_32:/home/jspooner/.local/share/Steam/ubuntu12_32/steam-runtime/i386/lib/i386-linux-gnu:/home/jspooner/.local/share/Steam/ubuntu12_32/steam-runtime/i386/lib:/home/jspooner/.local/share/Steam/ubuntu12_32/steam-runtime/i386/usr/lib/i386-linux-gnu:/home/jspooner/.local/share/Steam/ubuntu12_32/steam-runtime/i386/usr/lib:/home/jspooner/.local/share/Steam/ubuntu12_32/steam-runtime/amd64/lib/x86_64-linux-gnu:/home/jspooner/.local/share/Steam/ubuntu12_32/steam-runtime/amd64/lib:/home/jspooner/.local/share/Steam/ubuntu12_32/steam-runtime/amd64/usr/lib/x86_64-linux-gnu:/home/jspooner/.local/share/Steam/ubuntu12_32/steam-runtime/amd64/usr/lib::/usr/lib32SYSTEM_PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/gamesXDG_SESSION_PATH=/org/freedesktop/DisplayManager/Session1XDG_SEAT_PATH=/org/freedesktop/DisplayManager/Seat0SSH_AUTH_SOCK=/tmp/ssh-5Znf254kiOcD/agent.1438DEFAULTS_PATH=/usr/share/gconf/plasma.default.pathSESSION_MANAGER=local/jspooner-HP-ENVY-dv6-Notebook-PC:@/tmp/.ICE-unix/1769,unix/jspooner-HP-ENVY-dv6-Notebook-PC:/tmp/.ICE-unix/1769XDG_CONFIG_DIRS=/etc/xdg/xdg-plasma:/etc/xdg:/usr/share/kubuntu-default-settings/kf5-settingsPATH=/home/jspooner/.local/share/Steam/ubuntu12_32/steam-runtime/amd64/bin:/home/jspooner/.local/share/Steam/ubuntu12_32/steam-runtime/amd64/usr/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/gamesDESKTOP_SESSION=plasmaSTEAM_INSTALLED_BOOTSTRAP=1PWD=/home/jspooner/.local/share/SteamXDG_SESSION_TYPE=x11SDL_VIDEO_X11_DGAMOUSE=0KONSOLE_DBUS_WINDOW=/Windows/1LANG=en_US.UTF-8KDE_SESSION_UID=1000MANDATORY_PATH=/usr/share/gconf/plasma.mandatory.pathSYSTEM_
LD_LIBRARY_PATH=STEAMSCRIPT=/usr/bin/steamKONSOLE_DBUS_SESSION=/Sessions/1SHLVL=2XDG_SEAT=seat0COLORFGBG=15;0HOME=/home/jspoonerLANGUAGE=KDE_SESSION_VERSION=5STEAMSCRIPT_VERSION=100049XCURSOR_THEME=breeze_cursorsLOGNAME=jspoonerXDG_SESSION_DESKTOP=KDEDBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-tugGWXVkYX,guid=9d46ea3686fe0f6fbfadc8d35493b8dfXDG_DATA_DIRS=/usr/share:/usr/share/plasma:/usr/local/share/:/usr/share/LESSOPEN=| /usr/bin/lesspipe %sTEXTDOMAIN=steamDISPLAY=:0XDG_RUNTIME_DIR=/run/user/1000PROFILEHOME=QT_PLUGIN_PATH=/usr/lib/x86_64-linux-gnu/qt5/plugins:/lib/kde5/plugins/XDG_CURRENT_DESKTOP=KDEPAM_KWALLET_LOGIN=/tmp//jspooner.socketLESSCLOSE=/usr/bin/lesspipe %s %sTEXTDOMAINDIR=/usr/share/localeXAUTHORITY=/tmp/xauth-1000-_0_=/home/jspooner/.local/share/Steam/ubuntu12_32/steam \X!PXd4X 	V	dZ
OOf4338000-f43da000 r-xp 00000000 08:08 15480018                           /usr/lib32/libatiadlxx.so
f43da000-f43dc000 rw-p 000a2000 08:08 15480018                           /usr/lib32/libatiadlxx.so
f43dc000-f43ec000 rw-p 00000000 00:00 0 
f43f0000-f67a2000 r-xp 00000000 08:08 15600743                           /usr/lib32/fglrx/dri/fglrx_dri.so
f67a2000-f6892000 rw-p 023b1000 08:08 15600743                           /usr/lib32/fglrx/dri/fglrx_dri.so
f6892000-f6976000 rw-p 00000000 00:00 0 
f6978000-f6987000 r-xp 00000000 08:08 15480016                           /usr/lib32/libatiuki.so.1.0
f6987000-f6994000 rw-p 0000f000 08:08 15480016                           /usr/lib32/libatiuki.so.1.0
f6994000-f6995000 rw-p 00000000 00:00 0 
f6998000-f69ab000 r-xp 00000000 08:08 16389538                           /usr/lib/i386-linux-gnu/libXext.so.6.4.0
f69ab000-f69ac000 r--p 00012000 08:08 16389538                           /usr/lib/i386-linux-gnu/libXext.so.6.4.0
f69ac000-f69ad000 rw-p 00013000 08:08 16389538                           /usr/lib/i386-linux-gnu/libXext.so.6.4.0
f69b0000-f6a32000 r-xp 00000000 08:08 15480031                           /usr/lib32/fglrx/libGL.so.1.2
f6a32000-f6a3e000 rwxp 00082000 08:08 15480031                           /usr/lib32/fglrx/libGL.so.1.2
f6a3e000-f6a53000 rwxp 00000000 00:00 0 
f6a72000-f6a74000 rw-s 00002000 00:05 832                                /dev/ati/card0
f6a78000-f6aaf000 r-xp 00000000 08:08 12847347                           /home/jspooner/.local/share/Steam/ubuntu12_32/crashhandler.so
f6aaf000-f6ab0000 r--p 00037000 08:08 12847347                           /home/jspooner/.local/share/Steam/ubuntu12_32/crashhandler.so
f6ab0000-f6ab1000 rw-p 00038000 08:08 12847347                           /home/jspooner/.local/share/Steam/ubuntu12_32/crashhandler.so
f6ab1000-f6ab8000 rw-p 00000000 00:00 0 
f6abf000-f6e90000 rw-p 00000000 00:00 0 
f6e90000-f7090000 r--p 00000000 08:08 15080851                           /usr/lib/locale/locale-archive
f7090000-f7095000 r-xp 00000000 08:08 12847375                           /home/jspooner/.local/share/Steam/ubuntu12_32/steam-runtime/i386/usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
f7095000-f7096000 r--p 00004000 08:08 12847375                           /home/jspooner/.local/share/Steam/ubuntu12_32/steam-runtime/i386/usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
f7096000-f7097000 rw-p 00005000 08:08 12847375                           /home/jspooner/.local/share/Steam/ubuntu12_32/steam-runtime/i386/usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
f7098000-f709a000 r-xp 00000000 08:08 12847381                           /home/jspooner/.local/share/Steam/ubuntu12_32/steam-runtime/i386/usr/lib/i386-linux-gnu/libXau.so.6.0.0
f709a000-f709b000 r--p 00001000 08:08 12847381                           /home/jspooner/.local/share/Steam/ubuntu12_32/steam-runtime/i386/usr/lib/i386-linux-gnu/libXau.so.6.0.0
f709b000-f709c000 rw-p 00002000 08:08 12847381                           /home/jspooner/.local/share/Steam/ubuntu12_32/steam-runtime/i386/usr/lib/i386-linux-gnu/libXau.so.6.0.0
f70a0000-f70b9000 r-xp 00000000 08:08 12847418                           /home/jspooner/.local/share/Steam/ubuntu12_32/steam-runtime/i386/lib/i386-linux-gnu/libgcc_s.so.1
f70b9000-f70ba000 r--p 00018000 08:08 12847418                           /home/jspooner/.local/share/Steam/ubuntu12_32/steam-runtime/i386/lib/i386-linux-gnu/libgcc_s.so.1
f70ba000-f70bb000 rw-p 00019000 08:08 12847418                           /home/jspooner/.local/share/Steam/ubuntu12_32/steam-runtime/i386/lib/i386-linux-gnu/libgcc_s.so.1
f70c0000-f70e0000 r-xp 00000000 08:08 12847383                           /home/jspooner/.local/share/Steam/ubuntu12_32/steam-runtime/i386/usr/lib/i386-linux-gnu/libxcb.so.1.1.0
f70e0000-f70e1000 r--p 0001f000 08:08 12847383                           /home/jspooner/.local/share/Steam/ubuntu12_32/steam-runtime/i386/usr/lib/i386-linux-gnu/libxcb.so.1.1.0
f70e1000-f70e2000 rw-p 00020000 08:08 12847383                           /home/jspooner/.local/share/Steam/ubuntu12_32/steam-runtime/i386/usr/lib/i386-linux-gnu/libxcb.so.1.1.0
f70e8000-f7290000 r-xp 00000000 08:08 17181757                           /lib/i386-linux-gnu/libc-2.19.so
f7290000-f7292000 r--p 001a8000 08:08 17181757                           /lib/i386-linux-gnu/libc-2.19.so
f7292000-f7293000 rw-p 001aa000 08:08 17181757                           /lib/i386-linux-gnu/libc-2.19.so
f7293000-f7296000 rw-p 00000000 00:00 0 
f7298000-f72b0000 r-xp 00000000 08:08 17182249                           /lib/i386-linux-gnu/libpthread-2.19.so
f72b0000-f72b2000 r--p 00017000 08:08 17182249                           /lib/i386-linux-gnu/libpthread-2.19.so
f72b2000-f72b3000 rw-p 00019000 08:08 17182249                           /lib/i386-linux-gnu/libpthread-2.19.so
f72b3000-f72b5000 rw-p 00000000 00:00 0 
f72b8000-f7395000 r-xp 00000000 08:08 12847378                           /home/jspooner/.local/share/Steam/ubuntu12_32/steam-runtime/i386/usr/lib/i386-linux-gnu/libstdc++.so.6.0.18
f7395000-f7399000 r--p 000dc000 08:08 12847378                           /home/jspooner/.local/share/Steam/ubuntu12_32/steam-runtime/i386/usr/lib/i386-linux-gnu/libstdc++.so.6.0.18
f7399000-f739a000 rw-p 000e0000 08:08 12847378                           /home/jspooner/.local/share/Steam/ubuntu12_32/steam-runtime/i386/usr/lib/i386-linux-gnu/libstdc++.so.6.0.18
f739a000-f73a1000 rw-p 00000000 00:00 0 
f73a4000-f73a8000 rw-p 00000000 00:00 0 
f73a8000-f73ab000 r-xp 00000000 08:08 17182250                           /lib/i386-linux-gnu/libdl-2.19.so
f73ab000-f73ac000 r--p 00002000 08:08 17182250                           /lib/i386-linux-gnu/libdl-2.19.so
f73ac000-f73ad000 rw-p 00003000 08:08 17182250                           /lib/i386-linux-gnu/libdl-2.19.so
f73b0000-f73f4000 r-xp 00000000 08:08 17177142                           /lib/i386-linux-gnu/libm-2.19.so
f73f4000-f73f5000 r--p 00043000 08:08 17177142                           /lib/i386-linux-gnu/libm-2.19.so
f73f5000-f73f6000 rw-p 00044000 08:08 17177142                           /lib/i386-linux-gnu/libm-2.19.so
f73f8000-f73ff000 r-xp 00000000 08:08 17182251                           /lib/i386-linux-gnu/librt-2.19.so
f73ff000-f7400000 r--p 00006000 08:08 17182251                           /lib/i386-linux-gnu/librt-2.19.so
f7400000-f7401000 rw-p 00007000 08:08 17182251                           /lib/i386-linux-gnu/librt-2.19.so
f7404000-f7425000 rw-p 00000000 00:00 0 
f7425000-f7426000 r--p 002c5000 08:08 15080851                           /usr/lib/locale/locale-archive
f7426000-f7428000 rw-p 00000000 00:00 0 
f7428000-f7558000 r-xp 00000000 08:08 12847376                           /home/jspooner/.local/share/Steam/ubuntu12_32/steam-runtime/i386/usr/lib/i386-linux-gnu/libX11.so.6.3.0
f7558000-f7559000 r--p 00130000 08:08 12847376                           /home/jspooner/.local/share/Steam/ubuntu12_32/steam-runtime/i386/usr/lib/i386-linux-gnu/libX11.so.6.3.0
f7559000-f755b000 rw-p 00131000 08:08 12847376                           /home/jspooner/.local/share/Steam/ubuntu12_32/steam-runtime/i386/usr/lib/i386-linux-gnu/libX11.so.6.3.0
f755b000-f7560000 rw-p 00000000 00:00 0 
f7560000-f7580000 r-xp 00000000 08:08 17181755                           /lib/i386-linux-gnu/ld-2.19.so
f7580000-f7581000 r--p 0001f000 08:08 17181755                           /lib/i386-linux-gnu/ld-2.19.so
f7581000-f7582000 rw-p 00020000 08:08 17181755                           /lib/i386-linux-gnu/ld-2.19.so
f7582000-f7585000 rw-p 00000000 00:00 0 
f7585000-f7586000 r-xp 00000000 00:00 0                                  [vdso]
f7586000-f7588000 r--p 00000000 00:00 0                                  [vvar]
f7588000-f77e3000 r-xp 00000000 08:08 12847419                           /home/jspooner/.local/share/Steam/ubuntu12_32/steam
f77e3000-f77eb000 r--p 0025b000 08:08 12847419                           /home/jspooner/.local/share/Steam/ubuntu12_32/steam
f77eb000-f77f1000 rw-p 00263000 08:08 12847419                           /home/jspooner/.local/share/Steam/ubuntu12_32/steam
f77f1000-f7813000 rw-p 00000000 00:00 0 
f8bb6000-f8c5f000 rw-p 00000000 00:00 0                                  [heap]
ffb96000-ffbb8000 rw-p 00000000 00:00 0 

```

---

### Post by darksidedude on 2014-12-19
Ok so I had a breakthrew (sort of) I uninstalled the .run drivers from AMD and used the distro package. and I got it to run once. then upon reboot the next morning it won't run anymore throwing this error 

```
~$ steam
Running Steam on ubuntu 15.04 64-bit
STEAM_RUNTIME is enabled automatically
[2014-12-19 10:56:29] Startup - updater built Nov 21 2014 16:23:41
SteamUpdateUI: An X Error occurred
X Error of failed request:  BadValue (integer parameter out of range for operation) 
```

---

### Post by darksidedude on 2014-12-20
Got the problem fixed. it turns out while installing the ati drivers from the repo. apt did not pull in fglrx-amdcccle. I must assume that is important to the opperation to the graphics driver.

---

