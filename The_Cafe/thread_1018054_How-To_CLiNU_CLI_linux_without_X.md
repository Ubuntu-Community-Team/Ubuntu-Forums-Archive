---
title: "How-To :CLiNU CLI linux without X"
date: 2008-12-21
forum: The Cafe
---

### Post by Ioky on 2008-12-21
I have this idea for a long time, and I have finally put this into action. In  this guide, I documented What I did when I putting :CLiNU together. 

So for, this is like the first stage, it is all about testing each software, in order to determent what I want and what I don't want on the finally produce. So if you have any suggestion on anything, feel free to let me know. 

[here]("http://ubuntuforums.org/showthread.php?t=833627") is the list of CLI software I posted long time ago. 

	:CLiNU is a command line interface (CLI) based Linux/GNU distribution serve for general purposes. It blends a set of comprehensive applications, and tools, which allows users to accomplish everyday computing in a pure CLI environment. The name ":CLiNU" stands for CLI based Linux without X.org. It is light-weight, feature-rich, and &#65279;elegance. 

:CLiNU How-To @ ubuntu v0.1

Mission: Setup :CLiNU and test applications for further optimization and customization, use ubuntu (8.10) as the base system.

Part I: Install Ubuntu minimal

  Download the ubuntu alternate desktop CD and use F4 option install a CLI system.
  This can also be done with the ubuntu minimal CD.
  
  edit repository sources list
    sudo gedit /etc/apt/sources.list

  enable the medibuntu repository
    sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list
  
  import the gpg-key
    sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

  ruby is needed for some application
    sudo apt-get install ruby irb1.8

Part II: Install system tools

  The sytem tools will give the user more control with their CLI, such as easier file management and be able to switch between multi-applications. These packages are highly recommmanded.

  Install with the code: sudo apt-get install "name of the package" (read app list for detail)

  List of system tools:
    zsh = A shell with lots of features 
    screen = terminal multiplexor with VT100/ANSI terminal emulation 
    vlock = Virtual Console locking program 
    mc = Midnight Commander - a powerful file manager
    vifm = a ncurses based file manager with vi like keybindings
    fdisk = Partition editor for Acorn/RISC OS machines
    gpart = Guess PC disk partition table, find lost partitions
    alsa = ALSA driver 
      alsa-oss = ALSA wrapper for OSS applications
      alsa-tools = Console based ALSA utilities for specific hardware
    multitail = view multiple logfiles windowed on console
    rdup = utility to create a file list suitable for making backups
    pm-utils = utilities and scripts for power management 
    htop = interactive processes viewer
    powertop = Linux tool to find out what is using power on a laptop 

    The Software below can be install, however, they seem again the :CLiNU style, so they are not recommanded.

    None*

Part III: Install applications

  Here is the list of applications we are going to run/test on this system sort by category. For testing purposes, all the CLI applications yet found will be installed, however, not all of them will be included in the final produce as core package. 

  Install with code: sudo apt-get install "name of the package" (read app list for detail)

  Accessoris:
    espeak = A multi-lingual software speech synthesizer 
    speex = The Speex codec command line tools
    festival = General multi-lingual speech synthesis system
      festival-czech = Czech support for Festival speech synthesis system
      festival-freebsoft-utils = Festival extensions and utilities
    emacspeak = speech output interface to Emacs 
      emacspeak-ss = Emacspeak speech server for several synthesizers
    abook = text-based ncurses address book application
    antiword = Converts MS Word files to text and ps
    halibut = yet another free document preparation system
    tetex-base = TeX Live: teTeX transitional package
      tetex-bin = TeX Live: teTeX transitional package 
      tetex-extra = TeX Live: teTeX transitional package
    catdoc = MS-Word to TeX or plain text converter
    libwv-1.2-3 = Library for accessing Microsoft Word documents 
    wv = Programs for accessing Microsoft Word documents 
    bc = The GNU bc arbitrary precision calculator language 
    wcalc = A flexible command-line scientific calculator
    gnuplot = A command-line driven interactive plotting program
      gunplot-mode = Yet another Gnuplot mode for Emacs
      gunplot-nox = A command-line driven interactive plotting program
    fbgrab = Framebuffer grabber
    oleo = GNU spreadsheet program
    sc = Text-based spreadsheet with VI-like keybindings
    atool = A tool for managing file archives of various types
    zip = Archiver for .zip files 
    rar = Archiver for .rar files
    lha = lzh archiver (or jlha-utils = command-line lzh archiver written in Java)
    p7zip-full = 7zr file archiver with high compression ratio
    cmatrix = simulates the display from "The Matrix"
    sl = Correct you if you type `sl' by mistake 
    calcurse = text-based calendar and todo manager
    qemu = fast processor emulator

    The Software below can be install, however, they seem again the :CLiNU style, so they are not recommanded.

    **gpm = General Purpose Mouse interface

  Games: 
    bsdgames = a collection of classic textual unix games
      bsdgames-nonfree = rogue, the classic dungeon exploration game
    gnuchess = Plays a game of chess, either against the user or against itself
    netris = free, networked version of T*tris
    nethack-console = Text-based overhead view D&D-style adventure game
    slashem = A variant of Nethack
    angband = A single-player, text-based, dungeon simulation game
    dopewars = Make a fortune dealing drugs on the streets of New York
    empire = the war game of the century

    There are more Games avaliable in CLI, however, they are not packaged with ubuntu, and they be just download and play. Therefore, they are not include on this list. For example:

    Vitetris = a terminal-based Tetris clone

  Graphic:
    zgv = SVGAlib graphics viewer
    fbi = Linux frame buffer image viewer
    imagemagick = image manipulation programs 
    caca-utils = text mode graphics utilities
    libfreeimage3 = Support library for graphics image formats (library)
    tpp = text presentation program

  Internet:
    elinks = advanced text-mode WWW browser
    lynx = Text-mode WWW Browser
    links = Web browser running in text mode
    links2 = Web browser running in both graphics and text mode
    w3m = WWW browsable pager with excellent tables/frames support 
    gFTP-text = colored FTP client using GLib
    mutt = text-based mailreader supporting MIME, GPG, PGP and threading 
    elmo = text-based mail-reader supporting SMTP and POP3
    sendemail = email-from-console sending tool
    freetalk = A console based Jabber client
    naim = A console client for AOL Instant Messenger and IRC
    irssi = terminal based IRC client
    finch = text-based multi-protocol instant messaging client 
    tinyirc = a tiny IRC client
    centerim = A text-mode multi-protocol instant messenger client
    ekg = console Gadu Gadu client for UNIX systems
    newsbeuter = text mode rss feed reader with podcast support 
    podget = Podcast aggregrator/downloader optimized for cron
    Snownews = Text mode RSS newsreader
    slrn = threaded news reader (fast for slow links)
    rtorrent = ncurses BitTorrent client based on LibTorrent
    wget = retrieves files from the web
    lftp = Sophisticated command-line FTP/HTTP client programs 
    ncftp = A user-friendly and well-featured FTP client
    curl = Get a file from an HTTP, HTTPS or FTP server 
    iptraf = Interactive Colorful IP LAN Monitor 
    cryptcat = TCP/IP swiss army knife extended with twofish encryption
    tcpdump = A powerful tool for network monitoring and data acquisition 
    wireshark = network traffic analyzer
    aircrack-ng = wireless WEP/WPA cracking utilities
    kismet = Wireless 802.11b monitoring tool

  Development:
    vim = Vi IMproved - enhanced vi editor 
      vim-latexsuite = view, edit and compile LaTeX documents from within Vim
      vim-not = Vi IMproved - enhanced vi editor
      vim-perl = Vi IMproved - enhanced vi editor (transitional package)
      vim-python = Vi IMproved - enhanced vi editor (transitional package)
      vim-rails = Vi IMproved - enhanced vi editor (transitional package)
      vim-ruby = Vi IMproved - enhanced vi editor (transitional package)
      vime-tcl = Vi IMproved - enhanced vi editor (transitional package)
      vim-runtime = Vi IMproved - Runtime files 
      vim-vimoutliner = script for building an outline editor on top of Vim
    nano = free Pico clone with some new features 
    emacs = The GNU Emacs editor (metapackage) 
    cxref-emacs = Generates latex and HTML documentation for C programs
    build-essential = Informational list of build-essential packages 
    
    There are too many libraries to be listed. Therefore no library are included on this list.

  Media:
    mplayer-nogui = The Ultimate Movie Player For Linux
    vlc-nox = multimedia player and streamer (without X support)
    cplay = A front-end for various audio players
    mpd = Music Player Daemon 
    mpc = A command-line tool to interface MPD
    ncmpc = text based audio player
    mp3blaster = Full-screen console mp3 and Ogg Vorbis player
    moc = ncurses based console audio player
    cmus = Lightweight ncurses audio player
    herrie = Minimalistic audio player built upon Ncurses
    orpheus = light-weight text mode menu- and window-driven audio player
    abcde = A Better CD Encoder
    crip = terminal-based ripper/encoder/tagger tool
    shell-fm = console based player for last.fm radio streams
    mpg123 = MPEG layer 1/2/3 audio player
    sox = Swiss army knife of sound processing
    mp3wrap = Utility for MP3 wrapping (rolling multiple MP3s into one)
    mp3splt = Splits MP3 and Ogg Vorbis files without reencoding
    pytone = Music jukebox with advanced features for DJs and a text-mode user interface
    libdvdcss2 = lib needed to play DVD
    gstreamer0.10-plugins-* = GStreamer documentation for plugins (complete set)
    vorbis-tools = several Ogg Vorbis tools 
    
Part IV: Further customization
  There are few things here and there need to work before you can get the application running. Sense the How-To have not yet finish, feel free to input any suggest on anything. 

Part V: Simply enjoy it!

---

### Post by billgoldberg on 2008-12-21
I bookmarked this how to because of the big selection of cli apps.

---

### Post by sertse on 2008-12-21
You may want to look at this existing project first. :) It has similar goals, and some of your guide has already been implemented already.

INX (Is not X). [http://inx.maincontent.net/](http://inx.maincontent.net/) It is based on Hardy though.

---

### Post by chris4585 on 2008-12-21
will there be a livecd?

and I second the INX project, more help focused into one project trying to achieve the same goal seems better

but maybe you're going for something different in that case I offer you this

You may want to look at my own project, its called ultra-livecd, it creates a livecd with the programs you want on it

its still in development right now, if you insist on using it though, contact me for proper usage

[https://code.launchpad.net/~chris4585/ultra-livecd/code]("https://code.launchpad.net/~chris4585/ultra-livecd/code")

---

