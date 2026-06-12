---
title: "snaps wiped out - now needs email and email password"
date: 2016-08-01
forum: Ubuntu Development Version
---

### Post by ventrical on 2016-08-01
On yakkety, ubuntu-desktop I was trying a snap experiment and noticed that all my snaps were gone... and it advised me that I had to login with my e-mail and my e-mail password!!!!   oh .. ok .. mayby it wants my SSO password.

Anyways .. this is really wierd. so much time I am spending with  unity8 I have neglected  unity7 :)

```

ventrical@ventrical-MS-7850:~$ snap login --help
Usage:
  snap [OPTIONS] login email

The login command authenticates on snapd and the snap store and saves
credentials
into the ~/.snap/auth.json file. Further communication with snapd will then be
made
using those credentials.

Login only works for local users in the sudo, admin or wheel groups.

An account can be setup at https://login.ubuntu.com

Application Options:
      --version    print the version and exit

Help Options:
  -h, --help       Show this help message

[login command arguments]
  email:           login.ubuntu.com email to login as
ventrical@ventrical-MS-7850:~$ sudo snap login
error: the required argument `email` was not provided
ventrical@ventrical-MS-7850:~$ sudo snap login whatsizname@email.com
Password: 
error: cannot authenticate on snap store: Provided email/password is not correct.
ventrical@ventrical-MS-7850:~$ 


```

---

### Post by ventrical on 2016-08-01
ayyyyy .. fer frummping sake.....

```

ventrical@ventrical-MS-7850:~$ sudo snap login whatsizname@email.com
Password: 
Login successful
ventrical@ventrical-MS-7850:~$ snap find
error: cannot list snaps: cannot communicate with server: open /home/ventrical/.snap/auth.json: permission denied
ventrical@ventrical-MS-7850:~$ 

```

 so it wants SSO... but then it hicups on me .. :)

---

### Post by grahammechanical on 2016-08-02
Xenial unity 7 - snap find comes up with this

> graham@Ub1604:~$ snap find
error: cannot list snaps: empty query

man snap has this
> 
create-user
       Creates a local system user

       The create-user command creates a local system user with  the  username
       and SSH keys registered on the store account identified by the provided
       email address.

An account can be setup at [https://login.ubuntu.com](https://login.ubuntu.com).

And this
> 
login
       Authenticates on snapd and the store

       The  login  command authenticates on snapd and the snap store and saves
       credentials into the ~/.snap/auth.json file. Further communication with
       snapd will then be made using those credentials.

       Login only works for local users in the sudo, admin or wheel groups.

An account can be setup at [https://login.ubuntu.com](https://login.ubuntu.com).

There is now a snap command to buy snaps

This is getting too complicated to be simple. I have still got my installed snaps on Unity 7 and they load.

Regards.

---

### Post by ventrical on 2016-08-02
> **grahammechanical said:**
> Xenial unity 7 - snap find comes up with this



man snap has this


And this


There is now a snap command to buy snaps

This is getting too complicated to be simple. I have still got my installed snaps on Unity 7 and they load.

Regards.

+1

So  for ubuntu personal.img is anybody's guess.  Mama said there'll be days like this - there'll be days like this my mama said.  :)

regards..

---

### Post by ventrical on 2016-08-02
On one install (that I have not updated recently) I still have snaps installed:

```

ventrical@ventrical-MS-7798:~$ snap list
Name         Version               Rev  Developer           Notes
audovia      3.2.2                 9    songbuilder         -
gnuchess     1.0                   2    tomechangosubanana  -
htop         2.0.1                 16   maxiberta           -
krita        3.0-snap12            3    krita               -
libreoffice  5.2.0.0.beta2         x1                       devmode
tpad         1.1                   4    caozhen             -
ubuntu-core  16.04+20160419.20-55  109  canonical           -
vlc          daily                 3    caldav              -
webdm        0.17                  21   canonical           -
x11-apps     1                     2    chadmiller          -
ventrical@ventrical-MS-7798:~$ 

```

and

```

ventrical@ventrical-MS-7798:~$ snap find
Name                  Version                       Developer            Notes  Summary
ag-mcphail            1.0.1                         njmcphail            -      The Silver Searcher - mcphail's build and upstream git version
archaeopteryx         2                             redmar               -      Visualization, Analysis, and Editing of Phylogenetic Trees
balloon-pop           1.0                           1bsyl                -      balloon popper game & puzzle
blender-tpaw          2.77a                         tpaw                 -      Blender is the free and open source 3D creation suite.
bubble-pop            1.0                           1bsyl                -      bubble popper game & puzzle.
cactpot-solver        1.1                           cyborgcentral        -      A tool for finding the best mini-cactpot card choices
champ                 0.0.1~git                     si-dz0ny             -      Plex 2nd screen player
checkbox-snappy       0.9~s16                       ce-certification-qa  -      Testing tool for Snappy Ubuntu Core (best installed with --devmode for the moment)
ci-dice               0.1                           beisner              -      Console dice roller tool for CI pass/fail simulation
cla-check             0.1                           kyrofa               -      Check if Canonical's Contributor License Agreement has been signed
click-parser          3.0.5                         bhdouglass           -      Extract data from Ubuntu's click & snap packages
compass-straightedge  1                             caozhen              -      Construct geometric figures with compass-and-straightedge construction
conjure-up            2.0.0.7                       adam-stokes          -      Package runtime for conjure-up spells
connect4              1.0                           1bsyl                -      4 in a Line/Row game
cpustat               0.01.27-20160726-227-77e2615  cking-kernel-tools   -      periodic cpu utilization statistics
darktable-kyrofa      2.0.5snap1                    kyrofa               -      Virtual lighttable and darkroom for photographers
dash-shell            0.5.9                         anthonywong          -      POSIX-compliant shell
demo-amd64            1.1                           woodrow              -      AMD64 generic package
demo-wget             1.17.1                        woodrow              -      retrieves files from the web
dstat-jamiebennett    0.7.3                         jamiebennett         -      Dstat is a versatile replacement for vmstat, iostat, mpstat, netstat and ifstat.
electrum-tpaw         2.6.4-tpaw3                   tpaw                 -      Lightweight Bitcoin Client
explode-bricks        1.1                           1bsyl                -      very Simple Bricks game
fiemap                0.0.1                         cking-kernel-tools   -      file extent dumping tool
freecell-solitaire    1.0                           1bsyl                -      FreeCell Solitaire, card game
game-2048             1                             dholbach             -      2048 puzzle game
gnuchess              2.1                           tomechangosubanana   -      Plays a game of chess, includes GUI and CLI. Run "gnuchess.readme" for more information.
go16-lbo              1.6.3                         lbo                  -      Go programming language compiler
gtwang-demo           1.0                           gtwang               -      G.T.Wang demo application.
hello-bluet           0.1                           bluet                -      Qt Hello World example
hello-gabriell        0.1                           gabriell             -      Qt Hello World example
hello-sergiusens      1.0                           sergiusens           -      hello world example
hello-snap            0.01                          muhammad             -      GNU hello-snap, the "Hello, Snap!" snap
hello-stgraber        2.10                          stgraber             -      GNU Hello, the "hello world" snap
ipython-example       5.0.0                         frankban             -      Enhanced interactive Python shell
ivoks-vim             7.4                           ivoks                -      ivoks's VIM
jtiledownloader       0.6.1-1                       ogra                 -      Download OSM maps
juju-nskaggs          2.0-beta13                    nskaggs              -      juju client
kernelscan            0.0.1                         cking-kernel-tools   -      fast kernel source error message scanner
kt                    1.0                           bjf                  -      Ubuntu Kernel Team Tools
laidout               0.096.1-2                     ogra                 -      Desktop Publishing
languagetool          3.4-snap2                     vs                   -      LanguageTool
liteide-tpaw          x30.2-tpaw1                   tpaw                 -      LiteIDE is a simple, open source, cross-platform Go IDE.
livetuner             0.1                           cyborgcentral        -      a GUI for livestreamer
mahjong-game          1.0                           1bsyl                -      Mahjong game, a one-player game. Based on SDL2
minesweeper           1.0                           1bsyl                -      Minesweeper game
miniterm-joc          1                             jocave               -      pySerial miniterm in a snap
modem-manager         1.4.0-1                       canonical            -      ModemManager is a service which controls mobile broadband
mongo22               2.2.7                         niemeyer             -      MongoDB document-oriented database
mongo24               2.4.14                        niemeyer             -      MongoDB document-oriented database
mongo26               2.6.12                        niemeyer             -      MongoDB document-oriented database
mongo30               3.0.12                        niemeyer             -      MongoDB document-oriented database
mongo32               3.2.7                         niemeyer             -      MongoDB document-oriented database
mongo33               3.3.9                         niemeyer             -      MongoDB document-oriented database
mup-accounts          2016.07.01                    niemeyer             -      mup IRC and Telegram bot - account connection side
mup-plugins           2016.07.05                    niemeyer             -      mup IRC and Telegram bot - plugins side
neovim-kalikiana      0.1.4                         kalikiana            -      Vim-fork focused on extensibility and agility.
nethack               3.4.2-2                       ogra                 -      The popular nethack console adventure
nikola                7.7.11                        ralsina              -      A modular, fast, simple, static website and blog generator
nitrokey-app          0.4snap1                      nitrokey             -      Nitrokey Application
ntpserver             0.1                           cargonza             -      ntp server snap app
overlay               0.1                           kyrofa               -      Tools for assisting with debugging read-only squashfs snaps via overlayfs
packageproxy          0.1                           ogra                 -      approx based package proxy running on port 9999
pc                    16.04-0.2                     canonical            -      AMD64 generic package
pc-kernel             4.4.0-31                      canonical            -      The canonical generic amd64 kernel
pmr                   1.0.0                         stub                 -      Merge Proprosal processor for Launchpad
podpublish            20160610+git5ddfa04-1         flexiondotorg        -      A tool for encoding and publishing podcast content and assets
polonium              v0.5.1                        rgrannell1           -      Polonium is a stateless password manager based on PBKDF2.
qownnotes             16.08.0                       pbek                 -      Plain-text file notepad with markdown support and ownCloud integration
readtsc               0.0.1                         cking-kernel-tools   -      Intel x86 Time Stamp Counter read
reversu               1.0                           1bsyl                -      ReversU is strategy board game with black & white tokens
robomongo             0.9.0-rc9                     frankban             -      MongoDB management tool
rpgdiceroller         1.7                           quality-mix          -      A dice roller with simple GUI
rpgen                 v0.1.0                        rgrannell1           -      compile multiple scripts into a single cloud-init friendly script
serial-vault          0.7                           james                -      Serial Vault Service
simple-cprov          0.4                           cprov                -      This is a test snap
snapstore-example     0.3                           noise                -      Minimalist example snap store
so-hello-world        0.2                           shadowen             -      the old classic
solitaire             1.0                           1bsyl                -      usual Solitaire card game, as known as Patience or Klondike
speed-test            1.7.0.1                       bartaz               -      Test your internet connection speed and ping using speedtest.net from the CLI
spider-solitaire      1.0                           1bsyl                -      Spider Solitaire card game
sudoku-game           1.0                           1bsyl                -      Sudoku 9x9 game
taskwarrior-plars     2.5.1-1                       pwlars               -      feature-rich console based todo list manager
teatime               16.07                         paroj                -      Simple egg timer application for the Unity Desktop
test-snapd-tools      1.0                           canonical            -      Tools for testing the snapd application
tftp-hpa-jhobbs       0                             jason-hobbs          -      Trivial File Transfer Protocol Client
torgo                 1.3.0                         tros                 -      A Logo interpreter written in Java.
tuxguitar-vs          1.3.2-snap2                   vs                   -      TuxGuitar
u1test20160725        1.0                           u1test20160720       -      Simple dd like tool
u1test20160920        0.1                           u1test201607192      -      Summary of the most simple snap
uname-a               1.0                           hungnhp              -      The test "uname -a" snap
unofficial-hexchat    2.12.1                        diddledan            -      HexChat IRC Client
upnp-server           0.1.0                         ogra                 -      upload files with WebDAV and serve them via DLNA/UPnP
vlc                   daily                         videolan             -      The ultimate media player
vuze-vs               5.7.2.0-snap1                 vs                   -      Vuze is a powerful, open source, bittorrent client.
wallpaperdownloader   2.0                           egarcia              -      Download and manage your favorite wallpapers from the Internet
x86latency-test       0.0.1                         cking-kernel-tools   -      Intel x86 kernel timer latency test
x86rdrand-benchmark   0.0.1                         cking-kernel-tools   -      Intel x86 rdrand CPU benchmark
xcape-lbo             7fca364                       lbo                  -      Modify keys to act as other keys
xkcdpass-codersquid   0.1                           codersquid           -      Generate secure multiword passwords/passphrases, inspired by XKCD
xlsx                  git                           tealeg               -      Convert microsoft XLSX files into CSV files.
ventrical@ventrical-MS-7798:~$ 

```

 but I can't get the x11-apps snap to work so I can try out deb apps in containers. Seems this can only be done while on uniy8.

regards..

---

### Post by ventrical on 2016-08-20
Oddly enough I was filing against another bug and I noticed this text file report:

```

Error: command ['systemctl', 'status', '--full', 'isc-dhcp-server.service'] failed with exit code 3: &#9679; isc-dhcp-server.service - ISC DHCP IPv4 server
   Loaded: loaded (/lib/systemd/system/isc-dhcp-server.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Sat 2016-08-20 02:39:12 EDT; 6min ago
     Docs: man:dhcpd(8)
 Main PID: 3001 (code=exited, status=1/FAILURE)

Aug 20 02:39:12 ventrical-MS-7850 sh[3001]: Not configured to listen on any interfaces!
Aug 20 02:39:12 ventrical-MS-7850 sh[3001]: If you think you have received this message due to a bug rather
Aug 20 02:39:12 ventrical-MS-7850 sh[3001]: than a configuration issue please read the section on submitting
Aug 20 02:39:12 ventrical-MS-7850 sh[3001]: bugs on either our web page at www.isc.org or in the README file
Aug 20 02:39:12 ventrical-MS-7850 sh[3001]: before submitting a bug.  These pages explain the proper
Aug 20 02:39:12 ventrical-MS-7850 sh[3001]: process and the information we find helpful for debugging..
Aug 20 02:39:12 ventrical-MS-7850 sh[3001]: exiting.
Aug 20 02:39:12 ventrical-MS-7850 systemd[1]: isc-dhcp-server.service: Main process exited, code=exited, status=1/FAILURE
Aug 20 02:39:12 ventrical-MS-7850 systemd[1]: isc-dhcp-server.service: Unit entered failed state.
Aug 20 02:39:12 ventrical-MS-7850 systemd[1]: isc-dhcp-server.service: Failed with result 'exit-code'.
------
Error: command ['systemctl', 'status', '--full', 'snapd.refresh.service'] failed with exit code 3: &#9679; snapd.refresh.service - Automatically refresh installed snaps
   Loaded: loaded (/lib/systemd/system/snapd.refresh.service; static; vendor preset: enabled)
   Active: failed (Result: exit-code) since Sat 2016-08-20 02:39:05 EDT; 7min ago
     Docs: man:snap(1)
 Main PID: 2243 (code=exited, status=1/FAILURE)

Aug 20 02:39:05 ventrical-MS-7850 systemd[1]: Starting Automatically refresh installed snaps...
Aug 20 02:39:05 ventrical-MS-7850 snap[2243]: error: cannot list updates: cannot list snaps: cannot list updates: Post https://search.apps.ubuntu.com/api/v1/snaps/metadata: dial tcp: lookup search.apps.ubuntu.com: Temporary failure in name resolution
Aug 20 02:39:05 ventrical-MS-7850 systemd[1]: snapd.refresh.service: Main process exited, code=exited, status=1/FAILURE
Aug 20 02:39:05 ventrical-MS-7850 systemd[1]: Failed to start Automatically refresh installed snaps.
Aug 20 02:39:05 ventrical-MS-7850 systemd[1]: snapd.refresh.service: Unit entered failed state.
Aug 20 02:39:05 ventrical-MS-7850 systemd[1]: snapd.refresh.service: Failed with result 'exit-code'.


```

---

