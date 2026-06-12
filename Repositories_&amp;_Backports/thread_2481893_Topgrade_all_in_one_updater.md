---
title: "Topgrade all in one updater"
date: 2022-12-12
forum: Repositories &amp; Backports
---

### Post by #&amp;thj^% on 2022-12-12
I bad mouthed this in the general forums, and heard about it. :D
After using Topgrade for a few days now, **I've come to a different conclusion**, *_but one needs to make sure it is installed properly_* as intended.
```
topgrade -v
DEBUG Configuration at /home/me/.config/topgrade.toml
DEBUG Loaded configuration: ConfigFile { pre_sudo: None, pre_commands: Some({}), post_commands: None, commands: Some({}), git_repos: None, predefined_git_repos: None, disable: None, ignore_failures: None, remote_topgrades: None, remote_topgrade_path: None, ssh_arguments: None, git_arguments: None, tmux_arguments: None, set_title: None, display_time: None, assume_yes: None, yay_arguments: None, aura_aur_arguments: None, aura_pacman_arguments: None, no_retry: None, run_in_tmux: None, cleanup: None, notify_each_step: None, accept_all_windows_updates: None, skip_notify: None, bashit_branch: None, only: None, composer: Some(Composer { self_update: None }), brew: Some(Brew { greedy_cask: None, autoremove: None }), linux: Some(Linux { yay_arguments: None, aura_aur_arguments: None, aura_pacman_arguments: None, arch_package_manager: None, show_arch_news: None, trizen_arguments: None, pikaur_arguments: None, pamac_arguments: None, dnf_arguments: None, apt_arguments: None, enable_tlmgr: None, redhat_distro_sync: None, rpm_ostree: None, emerge_sync_flags: None, emerge_update_flags: None }), git: Some(Git { max_concurrency: None, arguments: None, repos: None, pull_predefined: None }), windows: Some(Windows { accept_all_updates: None, self_rename: None, open_remotes_in_new_terminal: None, enable_winget: None }), npm: Some(NPM { use_sudo: None }), yarn: None, vim: None, firmware: Some(Firmware { upgrade: None }), vagrant: None, flatpak: Some(Flatpak { use_sudo: None }), distrobox: Some(Distrobox { use_root: None, containers: None }) }
DEBUG Detected "/usr/bin/notify-send" as "notify-send"
DEBUG Version: 10.2.2
DEBUG OS: x86_64-unknown-linux-gnu
DEBUG Args { inner: ["topgrade", "-v"] }
DEBUG Binary path: Ok("/home/me/.cargo/bin/topgrade")
DEBUG Self Update: false
DEBUG Detected "/usr/bin/git" as "git"
DEBUG Cannot find "doas"
DEBUG Detected "/usr/bin/sudo" as "sudo"
DEBUG Cannot find "pwsh"
DEBUG Cannot find "powershell"
DEBUG Step "System update"

&#8213;&#8213; 09:08:33 - System update &#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;

```
I've run some hefty updates between openSUSE and Ubuntu Lunar and Arch, Arch hadn't been refreshed for a week or more, so there was a sizable amount of core applications and kernels, flatpaks,firmware, and git included.
For SUSE it was about the same amount of core applications and all others.

I'm not saying to install it, but I find it pretty stable for the three OS's I've used it on heavily.

Downside is that the installing instructions are not all the same for each distro, and there can cause issues when using the Topgrade utility.
Also Please be aware that **I don't use or have snapd installed, so I can't really speak on that matter**. I wouldn't recommend this for newer users though.
EXAMPLE: Ubuntu Lunar:
```
me on Mon Dec 12 at 10:03 AM in ~ branch: (HEAD) 
>> topgrade

&#8213;&#8213; 10:03:09 - System update &#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;
[sudo] password for me: 
&#9581;&#9472; Updating Package List &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9582;
&#9474;Updated:   http://us.archive.ubuntu.com/ubuntu devel/main amd64 Packages [1.4…&#9474;
&#9474;Updated:   http://us.archive.ubuntu.com/ubuntu devel/main amd64 DEP-11 Metada…&#9474;
&#9474;Updated:   http://us.archive.ubuntu.com/ubuntu devel/main amd64 c-n-f Metadat…&#9474;
&#9474;Updated:   http://us.archive.ubuntu.com/ubuntu devel/universe i386 Packages […&#9474;
&#9474;Updated:   http://us.archive.ubuntu.com/ubuntu devel/universe amd64 Packages …&#9474;
&#9474;Updated:   http://us.archive.ubuntu.com/ubuntu devel/universe Translation-en …&#9474;
&#9474;Updated:   http://us.archive.ubuntu.com/ubuntu devel/universe amd64 DEP-11 Me…&#9474;
&#9474;Updated:   http://us.archive.ubuntu.com/ubuntu devel/universe DEP-11 48x48 Ic…&#9474;
&#9474;Updated:   http://us.archive.ubuntu.com/ubuntu devel/universe DEP-11 64x64 Ic…&#9474;
&#9474;Updated:   http://us.archive.ubuntu.com/ubuntu devel/universe amd64 c-n-f Met…&#9474;
&#9474;Updated:   http://us.archive.ubuntu.com/ubuntu devel/multiverse amd64 DEP-11 …&#9474;
&#9474;Fetched 47.5 MB in 11s (3.0 MB/s)                                             &#9474;
&#9584;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9583;
================================================================================
 Upgrading                                                                      
================================================================================
  Package:                  Old Version:      New Version:               Size:  
  libexempi8                2.6.2-2           2.6.3-1                   515 KB  
  libxml-sax-expat-perl     0.51-1            0.51-2                      9 KB  
  python3-xcffib            0.11.1-2          0.11.1-4                   64 KB  
                                                                                
================================================================================
 Summary                                                                        
================================================================================
 Upgrade 3 Packages                                                             
                                                                                
 Total download size  588 KB   
 Disk space required   22 KB   
                               
Do you want to continue? [Y/n] 
&#9581;&#9472; Downloading… &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9582;
&#9474; Total Packages: 3/3                                                          &#9474;
&#9474; Last Completed: libexempi8_2.6.3-1_amd64.deb                                 &#9474;
&#9474; Time Remaining: 0:00:00 &#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473; 100.0% • 588.0/588.0 KB • 2.9 MB/s &#9474;
&#9584;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9583;
&#9581;&#9472; Updating Packages &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9582;
&#9474;Unpacking:  libexempi8:amd64 (2.6.3-1) over (2.6.2-2)                         &#9474;
&#9474;Unpacking:  libxml-sax-expat-perl (0.51-2) over (0.51-1)                      &#9474;
&#9474;Unpacking:  python3-xcffib (0.11.1-4) over (0.11.1-2)                         &#9474;
&#9474;Setting up: libexempi8:amd64 (2.6.3-1)                                        &#9474;
&#9474;Setting up: python3-xcffib (0.11.1-4)                                         &#9474;
&#9474;Setting up: libxml-sax-expat-perl (0.51-2)                                    &#9474;
&#9474;update-perl-sax-parsers: Registering Perl SAX parser XML::SAX::Expat with pri…&#9474;
&#9474;update-perl-sax-parsers: Updating overall Perl SAX parser modules info file   &#9474;
&#9474;Processing: triggers for man-db (2.11.1-1)                                    &#9474;
&#9474;Processing: triggers for libc-bin (2.36-0ubuntu4)                             &#9474;
&#9474;&#9581;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9582;&#9474;
&#9474;&#9474;&#10004; Running dpkg … &#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473; 100.0% • 0:00:00 • 7/7&#9474;&#9474;
&#9474;&#9584;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9583;&#9474;
&#9584;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9583;
Finished Successfully

&#8213;&#8213; 10:03:56 - Cargo &#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;
    Updating registry 'https://github.com/rust-lang/crates.io-index'

Package       Installed  Latest   Needs update
cargo-update  v11.1.1    v11.1.1  No
topgrade      v10.2.2    v10.2.2  No

No packages need updating.
Package  Installed  Latest  Needs update

No git packages need updating.
Overall updated 0 packages.

&#8213;&#8213; 10:04:01 - Flatpak User Packages &#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;
Looking for updates…

Nothing to do.

&#8213;&#8213; 10:04:01 - Flatpak System Packages &#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;
Looking for updates…


        ID                                            Branch Op Remote  Download
 1. [&#10003;] org.freedesktop.Platform.GL.nvidia-470-141-03 1.4    u  flathub 273.0*MB / 273.8*MB

Updates complete.

&#8213;&#8213; 10:05:58 - Firmware upgrades &#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;
Updating lvfs
Downloading…             [***************************************]
Downloading…             [***************************************]
Downloading…             [***************************************]
Successfully downloaded new metadata: 1 local device supported
Devices with no available firmware updates: 
 • System Firmware
 • UEFI Device Firmware
Devices with the latest available firmware version:
 • UEFI dbx
No updates available

&#8213;&#8213; 10:06:02 - Summary &#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;
System update: OK
config-update: OK
cargo: OK
Flatpak: OK
Firmware upgrades: OK
```
I am going to continue using Topgrade for more time to get a real sense of it's compatibility with the Linux distro's mentioned here. (But I don't foresee any future issues)
Just my thought here while it is nice to run only one command to keep my systems updated and stable one should monitor all it does vigilantly.
EXAMPLE openSUSE:
```
me on Mon Dec 12 at 09:08 AM in ~ branch: (HEAD) 
>> topgrade

&#8213;&#8213; 14:42:59 - System update &#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;
[sudo] password for root: 
Repository 'NVIDIA' is up to date.                                              
Repository 'Main Repository (NON-OSS)' is up to date.                           
Repository 'Main Repository (DEBUG)' is up to date.                             
Repository 'Main Repository (Sources)' is up to date.                           
Repository 'Main Repository (OSS)' is up to date.                               
Repository 'Main Update Repository' is up to date.                              
Repository 'multimedia:libs' is up to date.                                     
Repository 'multimedia:apps' is up to date.                                     
Repository 'KDE:Applications' is up to date.                                    
Repository 'home:malcolmlewis:openSUSE_General' is up to date.                  
Repository 'network' is up to date.                                             
Repository 'KDE:Frameworks5' is up to date.                                     
Repository 'home:medozas74' is up to date.                                      
Repository 'openSUSE:Tumbleweed' is up to date.                                 
Repository 'KDE:Qt5' is up to date.                                             
Repository 'home:junknot' is up to date.                                        
Repository 'vdr' is up to date.                                                 
Repository 'KDE:Qt:5.15' is up to date.                                         
Repository 'nordvpn' is up to date.                                             
Repository 'packman' is up to date.                                             
Retrieving repository 'packman-x86_64' metadata ..........................[done]
Building repository 'packman-x86_64' cache ...............................[done]
All repositories have been refreshed.
Loading repository data...
Reading installed packages...
Warning: You are about to do a distribution upgrade with all enabled repositories. Make sure these repositories are compatible before you continue. See 'man zypper' for more information about this command.
Computing distribution upgrade...

The following package is going to be upgraded:
  libpoppler126

1 package to upgrade.
Overall download size: 1.1 MiB. Already cached: 0 B. No additional space will be
used or freed after the operation.
Continue? [y/n/v/...? shows all options] (y): 
Retrieving package libpoppler126-22.12.0-7.1.x86_64
                                           (1/1),   1.1 MiB (  3.7 MiB unpacked)
Retrieving: libpoppler126-22.12.0-7.1.x86_64.rpm ............[done (14.1 KiB/s)]

Checking for file conflicts: .............................................[done]
(1/1) Installing: libpoppler126-22.12.0-7.1.x86_64 .......................[done]
There are running programs which still use files and libraries deleted or updated by recent upgrades. They should be restarted to benefit from the latest updates. Run 'zypper ps -s' to list these programs.
 

&#8213;&#8213; 14:43:34 - Cargo &#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;
    Updating registry 'https://github.com/rust-lang/crates.io-index'

Package       Installed  Latest   Needs update
cargo-update  v11.1.1    v11.1.1  No
topgrade      v10.2.2    v10.2.2  No

No packages need updating.
Package  Installed  Latest  Needs update

No git packages need updating.
Overall updated 0 packages.

&#8213;&#8213; 14:43:35 - pip3 &#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;
Requirement already satisfied: pip in /usr/lib/python3.10/site-packages (22.3.1)

&#8213;&#8213; 14:43:36 - Flatpak User Packages &#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;
Looking for updates…

Nothing to do.

&#8213;&#8213; 14:43:36 - Flatpak System Packages &#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;
Looking for updates…

Nothing to do.

&#8213;&#8213; 14:43:41 - Firmware upgrades &#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;
Updating lvfs
Downloading…             [***************************************]
Downloading…             [***************************************]
Downloading…             [***************************************]
Successfully downloaded new metadata: 1 local device supported
Devices with no available firmware updates: 
 • MSFT0001:00 04F3:3140
 • MZVLB256HBHQ-000L2
 • ST1000LM049-2GH172
 • ST500VT001-1K6142
 • ST500VT001-1K6142
 • System Firmware
 • UEFI Device Firmware
 • UOEOS Laptop Dock
 • USB2.1 Hub
 • Unifying Receiver
 • WD Blue SN570 500GB
 • WDC WD40NDZW-11BHVS1
 • WDC WD50NDZW-11A8JS1
Devices with the latest available firmware version:
 • UEFI dbx
No updates available

&#8213;&#8213; 14:43:55 - Summary &#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;
System update: OK
config-update: OK
cargo: OK
pip3: OK
Flatpak: OK
Firmware upgrades: OK


```

---

### Post by Paddy Landau on 2022-12-12
For new users, Ubuntu already has automatic updates built in, so there's no point to using topgrade. If you use flatpak, you can use the Gnome Software Store in place of the Ubuntu Store, because it updates both snap and flatpak.

---

### Post by #&amp;thj^% on 2022-12-18
Well this has proven to be a nice experience for me.
Tested on Arch, Debian Testing, openSUSE and a couple of Arch based systems.
It has more  complete options other than just snaps and flatpaks, It's a keeper for me.
It is still being maintained or at least a fork is: [https://github.com/topgrade-rs/topgrade](https://github.com/topgrade-rs/topgrade)
```
 me on Sun Dec 18 at 10:52 AM in ~ branch: (HEAD) 
>> topgrade

&#8213;&#8213; 11:13:06 - System update &#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;
[sudo] password for me: 
Hit:1 https://repo.nordvpn.com/deb/nordvpn/debian stable InRelease
Hit:2 https://download.sublimetext.com apt/stable/ InRelease
Hit:3 http://eddie.website/repository/apt stable InRelease
Get:4 https://deb.kaisenlinux.org kaisen-rolling InRelease [19.7 kB]
Fetched 19.7 kB in 1s (15.1 kB/s)                     
Reading package lists... Done
W: https://download.sublimetext.com/apt/stable/InRelease: Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details.
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

&#8213;&#8213; 11:13:14 - oh-my-zsh &#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;
Updating Oh My Zsh
         __                                     __   
  ____  / /_     ____ ___  __  __   ____  _____/ /_  
 / __ \/ __ \   / __ `__ \/ / / /  /_  / / ___/ __ \ 
/ /_/ / / / /  / / / / / / /_/ /    / /_(__  ) / / / 
\____/_/ /_/  /_/ /_/ /_/\__, /    /___/____/_/ /_/  
                        /____/                       

Oh My Zsh is already at the latest version.

To keep up with the latest news and updates, follow us on Twitter: @ohmyzsh
Want to get involved in the community? Join our Discord: Discord server
Get your Oh My Zsh swag at: Planet Argon Shop

&#8213;&#8213; 11:13:14 - Cargo &#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;
    Updating registry 'https://github.com/rust-lang/crates.io-index'

Package       Installed  Latest   Needs update
topgrade      v10.2.2    v10.2.4  Yes
cargo-update  v11.1.1    v11.1.1  No

Updating topgrade
  Downloaded topgrade v10.2.4
  Downloaded 1 crate (177.4 KB) in 0.70s
    Updating crates.io index
  Installing topgrade v10.2.4
  Downloaded itoa v1.0.5
  Downloaded serde_derive v1.0.151
  Downloaded unicode-ident v1.0.6
  Downloaded serde v1.0.151
  Downloaded proc-macro2 v1.0.49
  Downloaded rustversion v1.0.11
  Downloaded thiserror v1.0.38
  Downloaded thiserror-impl v1.0.38
  Downloaded semver v1.0.16
  Downloaded quote v1.0.23
  Downloaded syn v1.0.107
  Downloaded 11 crates (574.6 KB) in 0.75s
   Compiling libc v0.2.138
   Compiling proc-macro2 v1.0.49
   Compiling quote v1.0.23
   Compiling unicode-ident v1.0.6
   Compiling autocfg v1.1.0
   Compiling syn v1.0.107
   Compiling cfg-if v1.0.0
   Compiling once_cell v1.16.0
   Compiling version_check v0.9.4
   Compiling memchr v2.5.0
   Compiling lazy_static v1.4.0
   Compiling log v0.4.17
   Compiling pin-project-lite v0.2.9
   Compiling regex-syntax v0.6.28
   Compiling futures-core v0.3.25
   Compiling heck v0.4.0
   Compiling futures-task v0.3.25
   Compiling time-core v0.1.0
   Compiling futures-channel v0.3.25
   Compiling overload v0.1.1
   Compiling itoa v1.0.5
   Compiling bitflags v1.3.2
   Compiling futures-sink v0.3.25
   Compiling cc v1.0.78
   Compiling os_str_bytes v6.4.1
   Compiling futures-util v0.3.25
   Compiling smallvec v1.10.0
   Compiling rustversion v1.0.11
   Compiling serde_derive v1.0.151
   Compiling ppv-lite86 v0.2.17
   Compiling serde v1.0.151
   Compiling pin-utils v0.1.0
   Compiling futures-io v0.3.25
   Compiling termcolor v1.1.3
   Compiling strsim v0.10.0
   Compiling textwrap v0.15.2
   Compiling adler v1.0.2
   Compiling gimli v0.27.0
   Compiling eyre v0.6.8
   Compiling semver v1.0.16
   Compiling owo-colors v3.5.0
   Compiling thiserror v1.0.38
   Compiling dlv-list v0.3.0
   Compiling indenter v0.3.3
   Compiling rustc-demangle v0.1.21
   Compiling topgrade v10.2.4
   Compiling iana-time-zone v0.1.53
   Compiling bytes v1.3.0
   Compiling remove_dir_all v0.5.3
   Compiling roff v0.2.1
   Compiling same-file v1.0.6
   Compiling unicode-width v0.1.10
   Compiling either v1.8.0
   Compiling glob v0.3.0
   Compiling shell-words v1.1.0
   Compiling home v0.5.4
   Compiling sharded-slab v0.1.4
   Compiling tracing-core v0.1.30
   Compiling thread_local v1.1.4
   Compiling ahash v0.7.6
   Compiling proc-macro-error-attr v1.0.4
   Compiling proc-macro-error v1.0.4
   Compiling nu-ansi-term v0.46.0
   Compiling slab v0.4.7
   Compiling indexmap v1.9.2
   Compiling num-traits v0.2.15
   Compiling num-integer v0.1.45
   Compiling memoffset v0.6.5
   Compiling tokio v1.8.5
   Compiling time v0.3.17
   Compiling clap_lex v0.2.4
   Compiling miniz_oxide v0.6.2
   Compiling walkdir v2.3.2
   Compiling backtrace v0.3.67
   Compiling regex-automata v0.1.10
   Compiling tracing-log v0.1.3
   Compiling aho-corasick v0.7.20
   Compiling object v0.30.0
   Compiling matchers v0.1.0
   Compiling addr2line v0.19.0
   Compiling regex v1.5.6
   Compiling getrandom v0.2.8
   Compiling dirs-sys v0.3.7
   Compiling atty v0.2.14
   Compiling signal-hook-registry v1.4.0
   Compiling terminal_size v0.1.17
   Compiling num_cpus v1.14.0
   Compiling mio v0.7.14
   Compiling time v0.1.45
   Compiling nix v0.24.3
   Compiling which v4.1.0
   Compiling dirs v4.0.0
   Compiling directories v4.0.1
   Compiling rand_core v0.6.4
   Compiling console v0.15.2
   Compiling shellexpand v2.1.2
   Compiling chrono v0.4.23
   Compiling rand_chacha v0.3.1
   Compiling hashbrown v0.12.3
   Compiling rand v0.8.5
   Compiling ordered-multimap v0.4.3
   Compiling tempfile v3.2.0
   Compiling rust-ini v0.18.0
   Compiling tracing-attributes v0.1.23
   Compiling clap_derive v3.1.18
   Compiling futures-macro v0.3.25
   Compiling strum_macros v0.24.3
   Compiling thiserror-impl v1.0.38
   Compiling tracing v0.1.37
   Compiling tracing-subscriber v0.3.16
   Compiling strum v0.24.1
   Compiling clap v3.1.18
   Compiling tracing-error v0.2.0
   Compiling color-spantrace v0.2.0
   Compiling color-eyre v0.6.2
   Compiling clap_complete v3.1.4
   Compiling clap_mangen v0.1.7
   Compiling futures-executor v0.3.25
   Compiling futures v0.3.25
   Compiling toml v0.5.10
    Finished release [optimized] target(s) in 1m 51s
   Replacing /home/me/.cargo/bin/topgrade
    Replaced package `topgrade v10.2.2` with `topgrade v10.2.4` (executable `topgrade`)


Updated 1 package.
Package  Installed  Latest  Needs update

No git packages need updating.
Overall updated 1 package: topgrade.

&#8213;&#8213; 11:15:07 - Containers &#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;

&#8213;&#8213; 11:15:08 - Flatpak User Packages &#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;
Looking for updates&#8230;

Nothing to do.

&#8213;&#8213; 11:15:08 - Flatpak System Packages &#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;
Looking for updates&#8230;

(/usr/bin/flatpak update:601349): dconf-WARNING **: 11:15:09.314: unable to open file '/etc/dconf/db/kaisen': Failed to open file &#8220;/etc/dconf/db/kaisen&#8221;: open() failed: No such file or directory; expect degraded performance

Nothing to do.

&#8213;&#8213; 11:15:13 - Firmware upgrades &#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;

(fwupdmgr:601642): dconf-WARNING **: 11:15:13.877: unable to open file '/etc/dconf/db/kaisen': Failed to open file &#8220;/etc/dconf/db/kaisen&#8221;: open() failed: No such file or directory; expect degraded performance
Updating lvfs
Downloading&#8230;             [***************************************]
Successfully downloaded new metadata: 1 local device supported

(fwupdmgr:602181): dconf-WARNING **: 11:15:26.882: unable to open file '/etc/dconf/db/kaisen': Failed to open file &#8220;/etc/dconf/db/kaisen&#8221;: open() failed: No such file or directory; expect degraded performance
Devices with no available firmware updates: 
 &#8226; MSFT0001:00 04F3:3140
 &#8226; MZVLB256HBHQ-000L2
 &#8226; ST1000LM049-2GH172
 &#8226; ST500VT001-1K6142
 &#8226; ST500VT001-1K6142
 &#8226; System Firmware
 &#8226; UEFI Device Firmware
 &#8226; UOEOS Laptop Dock
 &#8226; USB2.1 Hub
 &#8226; Unifying Receiver
 &#8226; WD Blue SN570 500GB
 &#8226; WDC WD40NDZW-11BHVS1
 &#8226; WDC WD50NDZW-11A8JS1
Devices with the latest available firmware version:
 &#8226; UEFI dbx
No updates available

&#8213;&#8213; 11:15:26 - Vagrant boxes &#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;
No outdated boxes

&#8213;&#8213; 11:15:28 - Summary &#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;
System update: OK
config-update: OK
oh-my-zsh: OK
cargo: OK
Containers: OK
Flatpak: OK
Firmware upgrades: OK
Vagrant boxes: OK

```
I still agree newer users should use great caution though.

---

### Post by Paddy Landau on 2022-12-19
> **1fallen said:**
> Well this has proven to be a nice experience for me. …
That's interesting! I guess that it would work well on Ubuntu. I won't put it on my main machine, though, but if I get a little time, I might test it on a VM.

---

### Post by #&amp;thj^% on 2022-12-22
It's now been a week, I have used this on all OS's I've mentioned.
Conclusion Topgrade gets a Topgrade form me...:D

---

### Post by #&amp;thj^% on 2023-01-01
This make 3 weeks now, very solid program.
This is now in all my systems, and quite happy with it.
> **Paddy Landau said:**
> That's interesting! I guess that it would work well on Ubuntu. I won't put it on my main machine, though, but if I get a little time, I might test it on a VM. 
Yep not a hitch, it just works nicely.
```
me@me-ThinkPad-X1-Carbon-7th:~$ topgrade

&#8213;&#8213; 13:59:32 - System update &#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;
[sudo] password for me: 
Hit:1 http://eddie.website/repository/apt testing InRelease
Get:2 http://us.archive.ubuntu.com/ubuntu lunar InRelease [267 kB]             
Hit:3 http://security.ubuntu.com/ubuntu lunar-security InRelease               
Hit:4 https://repo.nordvpn.com//deb/nordvpn/debian stable InRelease            
Hit:5 https://ppa.launchpadcontent.net/ubuntuhandbook1/conkymanager2/ubuntu jammy InRelease
Hit:6 http://us.archive.ubuntu.com/ubuntu lunar-updates InRelease
Hit:7 http://us.archive.ubuntu.com/ubuntu lunar-backports InRelease
Get:8 http://us.archive.ubuntu.com/ubuntu lunar/main amd64 Packages [1,392 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu lunar/main i386 Packages [1,046 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu lunar/main Translation-en [511 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu lunar/main amd64 DEP-11 Metadata [444 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu lunar/main amd64 c-n-f Metadata [30.1 kB]
Get:13 http://us.archive.ubuntu.com/ubuntu lunar/universe amd64 Packages [14.8 MB]
Get:14 http://us.archive.ubuntu.com/ubuntu lunar/universe i386 Packages [7,845 kB]
Get:15 http://us.archive.ubuntu.com/ubuntu lunar/universe Translation-en [5,872 kB]
Get:16 http://us.archive.ubuntu.com/ubuntu lunar/universe amd64 DEP-11 Metadata [3,522 kB]
Get:17 http://us.archive.ubuntu.com/ubuntu lunar/universe DEP-11 48x48 Icons [3,473 kB]
Get:18 http://us.archive.ubuntu.com/ubuntu lunar/universe DEP-11 64x64 Icons [7,639 kB]
Get:19 http://us.archive.ubuntu.com/ubuntu lunar/universe amd64 c-n-f Metadata [299 kB]
Get:20 http://us.archive.ubuntu.com/ubuntu lunar/multiverse amd64 Packages [238 kB]
Get:21 http://us.archive.ubuntu.com/ubuntu lunar/multiverse amd64 DEP-11 Metadata [39.8 kB]
Get:22 http://us.archive.ubuntu.com/ubuntu lunar/multiverse amd64 c-n-f Metadata [8,716 B]
Fetched 47.4 MB in 9s (5,276 kB/s)                                             
Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following package was automatically installed and is no longer required:
  squashfs-tools
Use 'sudo apt autoremove' to remove it.
The following packages will be upgraded:
  less libcairo-gobject2 libcairo-script-interpreter2 libcairo2
  libdbusmenu-glib4 libdbusmenu-gtk3-4 libmpc3 lto-disabled-list
  python3-renderpm python3-reportlab python3-reportlab-accel python3-xkit
12 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,551 kB of archives.
After this operation, 2,048 B disk space will be freed.
Do you want to continue? [Y/n] 
Get:1 http://us.archive.ubuntu.com/ubuntu lunar/main amd64 less amd64 590-1.1 [140 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu lunar/main amd64 libcairo-script-interpreter2 amd64 1.16.0-7 [60.0 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu lunar/main amd64 libcairo-gobject2 amd64 1.16.0-7 [18.6 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu lunar/main amd64 libcairo2 amd64 1.16.0-7 [518 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu lunar/main amd64 libdbusmenu-glib4 amd64 18.10.20180917~bzr492+repack1-3ubuntu1 [45.1 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu lunar/main amd64 libdbusmenu-gtk3-4 amd64 18.10.20180917~bzr492+repack1-3ubuntu1 [30.2 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu lunar/main amd64 lto-disabled-list all 37 [12.2 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu lunar/main amd64 python3-renderpm amd64 3.6.12-1 [67.9 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu lunar/main amd64 python3-reportlab-accel amd64 3.6.12-1 [23.3 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu lunar/main amd64 python3-reportlab all 3.6.12-1 [564 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu lunar/main amd64 python3-xkit all 0.5.0ubuntu6 [17.4 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu lunar/main amd64 libmpc3 amd64 1.3.1-1 [54.1 kB]
Fetched 1,551 kB in 1s (1,829 kB/s)
(Reading database ... 188330 files and directories currently installed.)
Preparing to unpack .../00-less_590-1.1_amd64.deb ...
Unpacking less (590-1.1) over (590-1build1) ...
Preparing to unpack .../01-libcairo-script-interpreter2_1.16.0-7_amd64.deb ...
Unpacking libcairo-script-interpreter2:amd64 (1.16.0-7) over (1.16.0-6) ...
Preparing to unpack .../02-libcairo-gobject2_1.16.0-7_amd64.deb ...
Unpacking libcairo-gobject2:amd64 (1.16.0-7) over (1.16.0-6) ...
Preparing to unpack .../03-libcairo2_1.16.0-7_amd64.deb ...
Unpacking libcairo2:amd64 (1.16.0-7) over (1.16.0-6) ...
Preparing to unpack .../04-libdbusmenu-glib4_18.10.20180917~bzr492+repack1-3ubuntu1_amd64.deb ...
Unpacking libdbusmenu-glib4:amd64 (18.10.20180917~bzr492+repack1-3ubuntu1) over (16.04.1+22.10.20220928.1-0ubuntu1) ...
Preparing to unpack .../05-libdbusmenu-gtk3-4_18.10.20180917~bzr492+repack1-3ubuntu1_amd64.deb ...
Unpacking libdbusmenu-gtk3-4:amd64 (18.10.20180917~bzr492+repack1-3ubuntu1) over (16.04.1+22.10.20220928.1-0ubuntu1) ...
Preparing to unpack .../06-lto-disabled-list_37_all.deb ...
Unpacking lto-disabled-list (37) over (36) ...
Preparing to unpack .../07-python3-renderpm_3.6.12-1_amd64.deb ...
Unpacking python3-renderpm:amd64 (3.6.12-1) over (3.6.11-1build1) ...
Preparing to unpack .../08-python3-reportlab-accel_3.6.12-1_amd64.deb ...
Unpacking python3-reportlab-accel:amd64 (3.6.12-1) over (3.6.11-1build1) ...
Preparing to unpack .../09-python3-reportlab_3.6.12-1_all.deb ...
Unpacking python3-reportlab (3.6.12-1) over (3.6.11-1build1) ...
Preparing to unpack .../10-python3-xkit_0.5.0ubuntu6_all.deb ...
Unpacking python3-xkit (0.5.0ubuntu6) over (0.5.0ubuntu5) ...
Preparing to unpack .../11-libmpc3_1.3.1-1_amd64.deb ...
Unpacking libmpc3:amd64 (1.3.1-1) over (1.2.1-2build1) ...
Setting up lto-disabled-list (37) ...
Setting up python3-renderpm:amd64 (3.6.12-1) ...
Setting up libdbusmenu-glib4:amd64 (18.10.20180917~bzr492+repack1-3ubuntu1) ...
Setting up less (590-1.1) ...
Setting up libcairo2:amd64 (1.16.0-7) ...
Setting up python3-reportlab-accel:amd64 (3.6.12-1) ...
Setting up libmpc3:amd64 (1.3.1-1) ...
Setting up python3-reportlab (3.6.12-1) ...
Setting up libcairo-gobject2:amd64 (1.16.0-7) ...
Setting up python3-xkit (0.5.0ubuntu6) ...
Setting up libcairo-script-interpreter2:amd64 (1.16.0-7) ...
Setting up libdbusmenu-gtk3-4:amd64 (18.10.20180917~bzr492+repack1-3ubuntu1) ...
Processing triggers for man-db (2.11.1-1) ...
Processing triggers for mailcap (3.70+nmu1ubuntu1) ...
Processing triggers for libc-bin (2.36-0ubuntu4) ...

&#8213;&#8213; 14:00:04 - Cargo &#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;
    Updating registry 'https://github.com/rust-lang/crates.io-index'

Package       Installed  Latest   Needs update
cargo-update  v11.1.1    v11.1.1  No
topgrade      v10.2.4    v10.2.4  No

No packages need updating.
Package  Installed  Latest  Needs update

No git packages need updating.
Overall updated 0 packages.

&#8213;&#8213; 14:00:06 - Flatpak User Packages &#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;
Looking for updates&#8230;

Nothing to do.

&#8213;&#8213; 14:00:06 - Flatpak System Packages &#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;
Looking for updates&#8230;


        ID                                       Branch Op Remote  Download
 1. [&#10003;] com.github.micahflee.torbrowser-launcher stable u  flathub 355.3*kB / 8.0*MB

Updates complete.

&#8213;&#8213; 14:00:18 - Firmware upgrades &#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;
Updating lvfs
Downloading&#8230;             [***************************************]
Successfully downloaded new metadata: 4 local devices supported
Devices with no available firmware updates: 
 &#8226; Thunderbolt host controller
 &#8226; UEFI Device Firmware
 &#8226; UEFI Device Firmware
 &#8226; WD Blue SN570 500GB
Devices with the latest available firmware version:
 &#8226; Embedded Controller
 &#8226; System Firmware
 &#8226; UEFI Device Firmware
 &#8226; UEFI dbx
No updates available

&#8213;&#8213; 14:00:20 - Summary &#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;
System update: OK
config-update: OK
cargo: OK
Flatpak: OK
Firmware upgrades: OK

```
Just make sure it is installed correctly, that will make or break the whole experience.;)
**EDIT:4-6-2023 still a keeper**

---

