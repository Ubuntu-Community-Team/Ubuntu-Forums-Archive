---
title: "Upgrade from 14.04 to 16.04 failed"
date: 2016-07-22
forum: Server Platforms
---

### Post by deepakdeshp on 2016-07-22
Hello 

The upgrade has failed.

[https://forums.linuxmint.com/viewtopic.php?f=46&t=226015&sid=63aad7cf8626656a5bbc4c49365a71d5](https://forums.linuxmint.com/viewtopic.php?f=46&t=226015&sid=63aad7cf8626656a5bbc4c49365a71d5)

Please help

---

### Post by QIII on 2016-07-22
Please do not ask the community to go to a different forum to find out what your problem is.

Have the courtesy to describe your problem here in its entirety.

---

### Post by deepakdeshp on 2016-07-23
> **deepakdeshp said:**
> Hello 

The upgrade has failed.

[https://forums.linuxmint.com/viewtopic.php?f=46&t=226015&sid=63aad7cf8626656a5bbc4c49365a71d5](https://forums.linuxmint.com/viewtopic.php?f=46&t=226015&sid=63aad7cf8626656a5bbc4c49365a71d5)

Please help

My apology . I had posted from my mobile which did not let me format the post like using quotes or code etc. Here is the problem.

Hello,


I am trying to upgrade 32 bit Ubuntu server from 14.04 t0 16.04 which is running as a VM under Mint 18. But I am getting error. Please suggest the next steps


```

[SIZE=3]***sudo apt-get update***[/SIZE]
Hit http://security.ubuntu.com trusty-security InRelease
Ign http://ppa.launchpad.net trusty InRelease 
Ign http://us.archive.ubuntu.com trusty InRelease                      
Hit http://ppa.launchpad.net trusty Release.gpg                      
Hit http://security.ubuntu.com trusty-security/main Sources          
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://security.ubuntu.com trusty-security/restricted Sources      
Hit http://us.archive.ubuntu.com trusty-updates InRelease             
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://security.ubuntu.com trusty-security/universe Sources       
Hit http://us.archive.ubuntu.com trusty-backports InRelease                    
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://security.ubuntu.com trusty-security/multiverse Sources     
Get:1 http://us.archive.ubuntu.com trusty Release.gpg [933 B]
Hit http://us.archive.ubuntu.com trusty-updates/main Sources
Hit http://security.ubuntu.com trusty-security/main i386 Packages  
Hit http://us.archive.ubuntu.com trusty-updates/restricted Sources  
Hit http://security.ubuntu.com trusty-security/restricted i386 Packages
Hit http://us.archive.ubuntu.com trusty-updates/universe Sources    
Hit http://security.ubuntu.com trusty-security/universe i386 Packages
Hit http://security.ubuntu.com trusty-security/multiverse i386 Packages
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Sources 
Hit http://security.ubuntu.com trusty-security/main Translation-en
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en  
Get:2 http://us.archive.ubuntu.com trusty-updates/main i386 Packages [765 kB]
Hit http://security.ubuntu.com trusty-security/restricted Translation-en       
Hit http://security.ubuntu.com trusty-security/universe Translation-en         
Get:3 http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages [15.6 kB]
Get:4 http://us.archive.ubuntu.com trusty-updates/universe i386 Packages [365 kB]
Get:5 https://apt.dockerproject.org ubuntu-wily InRelease                      
Get:6 https://apt.dockerproject.org ubuntu-precise/main i386 Packages          
Get:7 https://apt.dockerproject.org ubuntu-precise/main Translation-en_US      
Get:8 https://apt.dockerproject.org ubuntu-trusty/main Translation-en_US       
Get:9 https://apt.dockerproject.org ubuntu-vivid/main Translation-en_US        
Get:10 https://apt.dockerproject.org ubuntu-wily/main Translation-en_US        
Ign https://apt.dockerproject.org ubuntu-precise/main Translation-en_US        
Ign https://apt.dockerproject.org ubuntu-precise/main Translation-en           
Ign https://apt.dockerproject.org ubuntu-trusty/main Translation-en_US         
Ign https://apt.dockerproject.org ubuntu-trusty/main Translation-en            
Ign https://apt.dockerproject.org ubuntu-vivid/main Translation-en_US          
Ign https://apt.dockerproject.org ubuntu-vivid/main Translation-en             
Ign https://apt.dockerproject.org ubuntu-wily/main Translation-en_US           
Ign https://apt.dockerproject.org ubuntu-wily/main Translation-en              
Get:11 http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages [13.6 kB]
Get:12 http://us.archive.ubuntu.com trusty-updates/main Translation-en [401 kB]
Get:13 http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en [7,227 B]
Get:14 http://us.archive.ubuntu.com trusty-updates/restricted Translation-en [3,699 B]
Get:15 http://us.archive.ubuntu.com trusty-updates/universe Translation-en [191 kB]
Hit http://us.archive.ubuntu.com trusty-backports/main Sources                 
Hit http://us.archive.ubuntu.com trusty-backports/restricted Sources           
Hit http://us.archive.ubuntu.com trusty-backports/universe Sources             
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Sources           
Hit http://us.archive.ubuntu.com trusty-backports/main i386 Packages           
Hit http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages     
Hit http://us.archive.ubuntu.com trusty-backports/universe i386 Packages       
Hit http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages     
Hit http://us.archive.ubuntu.com trusty-backports/main Translation-en          
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en    
Hit http://us.archive.ubuntu.com trusty-backports/restricted Translation-en    
Hit http://us.archive.ubuntu.com trusty-backports/universe Translation-en      
Hit http://us.archive.ubuntu.com trusty Release                                
Hit http://us.archive.ubuntu.com trusty/main Sources                           
Hit http://us.archive.ubuntu.com trusty/restricted Sources                     
Hit http://us.archive.ubuntu.com trusty/universe Sources                       
Hit http://us.archive.ubuntu.com trusty/multiverse Sources                     
Hit http://us.archive.ubuntu.com trusty/main i386 Packages                     
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages               
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages                 
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages               
Hit http://us.archive.ubuntu.com trusty/main Translation-en                    
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en              
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en              
Hit http://us.archive.ubuntu.com trusty/universe Translation-en                
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US                 
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US             
Fetched 1,090 kB in 4min 27s (4,070 B/s)                                       
Reading package lists... Done
uma@ubuntu-i386:~$[SIZE=4]_** sudo apt-get upgrade**_[/SIZE]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  libhdb9-heimdal libkdc2-heimdal libntdb1 python-ntdb
Use 'apt-get autoremove' to remove them.
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
uma@ubuntu-i386:~$ [SIZE=4]***/usr/bin/do-release-upgrade -c -d***[/SIZE]
Checking for a new Ubuntu release
New release '16.04 LTS' available.
Run 'do-release-upgrade' to upgrade to it.
uma@ubuntu-i386:~$ 
uma@ubuntu-i386:~$[SIZE=4]*** do-release-upgrade***[/SIZE]
Checking for a new Ubuntu release
No new release found



```




The upgrade script is as follows,


```
cat /usr/bin/do-release-upgrade
#!/usr/bin/python3


from __future__ import print_function


import warnings
warnings.filterwarnings("ignore", "apt API not stable yet", FutureWarning)


from DistUpgrade.DistUpgradeVersion import VERSION


from UpdateManager.Core.MetaRelease import MetaReleaseCore
from optparse import OptionParser
import locale
import gettext


import os
import sys
import time
from UpdateManager.Core.utils import init_proxy


RELEASE_AVAILABLE=0
NO_RELEASE_AVAILABLE=1




def get_fetcher(frontend, new_dist, datadir):
    if frontend == "DistUpgradeViewGtk3":
        from DistUpgrade.DistUpgradeFetcher import DistUpgradeFetcherGtk
        from DistUpgrade.GtkProgress import GtkAcquireProgress
        progress = GtkAcquireProgress(
            None,
            datadir,
            _("Downloading the release upgrade tool"))
        return DistUpgradeFetcherGtk(new_dist=new_dist,
                                     progress=progress,
                                     parent=None,
                                     datadir=datadir)
    else:
        from DistUpgrade.DistUpgradeFetcherCore import DistUpgradeFetcherCore
        import apt
        progress = apt.progress.text.AcquireProgress()
        return DistUpgradeFetcherCore(new_dist, progress)




if __name__ == "__main__":


  #FIXME: Workaround a bug in optparser which doesn't handle unicode/str
  #       correctly, see http://bugs.python.org/issue4391
  #       Should be resolved by Python3
  gettext.bindtextdomain("ubuntu-release-upgrader", "/usr/share/locale")
  gettext.textdomain("ubuntu-release-upgrader")
  translation = gettext.translation("ubuntu-release-upgrader", fallback=True)
  if sys.version >= '3':
    _ = translation.gettext
  else:
    _ = translation.ugettext


  try:
    locale.setlocale(locale.LC_ALL, "")
  except:
    pass


  init_proxy()


  # when run as "check-new-release" we go into "check only" mode
  check_only = sys.argv[0].endswith("check-new-release")


  parser = OptionParser()
  parser.add_option ("-V", "--version", action="store_true",
                     dest="show_version", default=False,
                     help=_("Show version and exit"))
  parser.add_option ("-d", "--devel-release", action="store_true",
                     dest="devel_release", default=False,
                     help=_("Check if upgrading to the latest devel release "
                          "is possible"))
  parser.add_option ("--data-dir", "",
                     default="/usr/share/ubuntu-release-upgrader/",
                     help=_("Directory that contains the data files"))
  parser.add_option ("-p", "--proposed", action="store_true",
                     dest="proposed_release", default=False,
                     help=_("Try upgrading to the latest release using "
                            "the upgrader from $distro-proposed"))
  parser.add_option ("-m", "--mode", default="server",
                     dest="mode", 
                     help=_("Run in a special upgrade mode.\n"
                            "Currently 'desktop' for regular upgrades of "
                            "a desktop system and 'server' for server "
                            "systems are supported."))
  parser.add_option ("-f", "--frontend", default="DistUpgradeViewText",
                     dest="frontend", 
                     help=_("Run the specified frontend"))
  parser.add_option ("-s","--sandbox", action="store_true", default=False,
                     help=_("Test upgrade with a sandbox aufs overlay"))
  parser.add_option ("-c", "--check-dist-upgrade-only", action="store_true",
                     default=check_only,
                     help=_("Check only if a new distribution release is "
                            "available and report the result via the "
                            "exit code"))
  parser.add_option ("-q", "--quiet", default=False, action="store_true",
                     dest="quiet")


  (options, args) = parser.parse_args()




  if options.show_version:
    print("%s: version %s" % (os.path.basename(sys.argv[0]), VERSION))
    sys.exit(0)


  if options.devel_release and options.proposed_release:
    print(_("The options --devel-release and --proposed are"))
    print(_("mutually exclusive. Please use only one of them."))
    sys.exit(1)


  if not options.quiet:
    print(_("Checking for a new Ubuntu release"))


  m = MetaReleaseCore(useDevelopmentRelease=options.devel_release,
                      useProposed=options.proposed_release)
  # this will timeout eventually
  m.downloaded.wait()


  # make sure to inform the user if his distro is no longer supported
  # this will make it appear in motd (that calls do-release-upgrade in
  #  check-new-release mode)
  if m.no_longer_supported is not None:
    url = "http://www.ubuntu.com/releaseendoflife"
    print(_("Your Ubuntu release is not supported anymore."))
    print(_("For upgrade information, please visit:\n"
            "%(url)s\n") % { 'url' : url })


  # now inform about a new release
  if m.new_dist is None:
    if not options.quiet:
      print(_("No new release found"))
    sys.exit(NO_RELEASE_AVAILABLE)


  if m.new_dist.upgrade_broken:
    if not options.quiet:
      print(_("Release upgrade not possible right now"))
      print(_("The release upgrade can not be performed currently, "
              "please try again later. The server reported: '%s'") % m.new_dist.upgrade_broken)
    sys.exit(NO_RELEASE_AVAILABLE)


  # we have a new dist
  if options.check_dist_upgrade_only:
    print(_("New release '%s' available.") % m.new_dist.version)
    print(_("Run 'do-release-upgrade' to upgrade to it."))
    sys.exit(RELEASE_AVAILABLE)


  fetcher = get_fetcher(options.frontend, m.new_dist, options.data_dir)
  fetcher.run_options += ["--mode=%s" % options.mode,
                          "--frontend=%s" % options.frontend,
                          ]
  if options.sandbox:
    fetcher.run_options.append("--sandbox")
  if options.devel_release:
    fetcher.run_options.append("--devel-release")
  fetcher.run()



```

---

### Post by darkod on 2016-07-23
This is normal. DO NOT run do-release-upgrade with the -d option, that is used also for upgrading to development releases and can mess things up. When you run only do-release-upgrade it says no upgrade found which is correct because upgrading from LTS to LTS is available only after the .1 release of the new LTS. In other words, you will be able to upgrade from 14.04.x to 16.04 only after 16.04.1 is released (which should be August). So in fact, you will be upgrading directly to 16.04.1.

I think they do this because for production environments it is better anyway to wait for the .1 to be released because it will contain any fixes for problems noticed in 16.04.

After it's available your OS will prompt you with a message if you want to upgrade, don't worry.

---

### Post by deepakdeshp on 2016-07-23
> So in fact, you will be upgrading directly to 16.04.1.

I think they do this because for production environments it is better anyway to wait for the .1 to be released because it will contain any fixes for problems noticed in 16.04.

After it's available your OS will prompt you with a message if you want to upgrade, don't worry.

Thank you.

---

