---
title: "How To: µTorrent Server"
date: 2014-11-19
forum: Tutorials
---

### Post by Rich.T. on 2014-11-19
[SIZE=7]**How To: µTorrent Server**[/SIZE]
[SIZE=4][COLOR="#800000"]How To install and Configure µTorrent Server alpha-v3_3 on Ubuntu.[/COLOR][/SIZE]

[B]After installing and playing around with µTorrent Server for a couple of days, I have settled on a methodology and thought I'd share it with you all.
I have included a configuration file which has the following options set:

[COLOR="#800000"][LIST]
[*]dir_active: /home/<USERNAME>/Bittorrent/
[*]dir_completed: /home/<USERNAME>/Bittorrent/Completed/
[*]dir_torrent_files: /home/<USERNAME>/.utserver/dottorrent/
[*]dir_autoload: /home/<USERNAME>/.utserver/dottorrent/autoload/
[*]dir_request: /home/<USERNAME>/.utserver/request/
[*]admin_name: <USERNAME>
[*]admin_password: <PASSWORD>
[*]ut_webui_dir: /opt/utorrent-server-alpha-v3_3/
[*]low_cpu: 1
[*]prealloc_space: 1
[*]randomize_bind_port: 1
[*]max_ul_rate: 5000
[*]max_ul_rate_seed: 500
[*]seed_ratio: 200
[/LIST][/COLOR]
NB: <USERNAME> throughout this tutorial should be replaced with your own user name, i.e. the name on your home directory.
and  <PASSWORD> should be a strong and unique one of your own making.
Just cut'n'paste the relevent bits into a decent text editor/IDE and search/replace the <ENTRY> with your own.

Feel free to change these or any other settings. Explanations of what these do are included in the configuration file.
[COLOR="#800000"]Also, please feel free to replace "vim" with a text editor/IDE of your choice: I particularly favour Geany; it's great![/COLOR][/B]

[SIZE=5]How To Install µTorrent Server[/SIZE]

Links:
[http://www.utorrent.com/downloads/linux](http://www.utorrent.com/downloads/linux)
[http://www.utorrent.com/downloads/complete/type/utserver/os/linux-x64-ubuntu-13-04/track/beta](http://www.utorrent.com/downloads/complete/type/utserver/os/linux-x64-ubuntu-13-04/track/beta)

Download from the link above then do the following:

```
sudo cp utserver.tar.gz /opt/
cd /opt/
sudo tar -xvf utserver.tar.gz
```

After extracting the tar file, remove it.

```
sudo rm -rf utserver.tar.gz
```

The first thing to do now is to make the directories needed to store your torrents, .torrent files, log files and configuration files:

```
mkdir -p /home/<USERNAME>/Bittorrent/Completed/
mkdir -p /home/<USERNAME>/.utserver/dottorrent/autoload/
mkdir /home/<USERNAME>/.utserver/request/
```

Now, it would be in your interest to create a customised configuration file to pre-set the most important options for µTorrent Server.
This is not entirely neccessary, as you can set all of this from the settings menu of the Web UI and these are persistent.
However, it will save time and effort later and also teach you what the various settings and command line options we are using are for.

Create the config file:

```
vim /home/<USERNAME>/.utserver/utserver.conf
```

```
##
## utserver.conf
## Configuration settings template for &#956;Torrent for Linux.
## Taken from &#956;Torrent Server manual for version alpha-3.3.
## ©2013 BitTorrent, Inc.
## Compiled by Rich.T.
##

##
## Command-line Arguments
##

## µTorrent Server supports the following arguments - the keywords are
## case-insensitive and should be immediately preceded with a dash (-):

## &#9633; configfile - path to and name of the configuration file - if this
##   argument is not specified, the utserver program looks for a file named
##   utserver.conf in the current working directory - see the following
##   section for more details
## &#9633; logfile - path to and name of the log file - specifying -logfile
##   filename will direct log output to filename, while specifying -logfile
##   without a filename will direct log file output to utserver.log in the
##   current working directory
## &#9633; settingspath - path to directory to store files of relatively small
##   size (operational settings, torrent resume information, RSS feed
##   information) - if not specified, the utserver program will store these
##   files in the current working directory
## &#9633; pidfile - path to and name of the file to create that will contain the
##   process ID of the utserver process
## &#9633; daemon - directs the server to run in its own process group
## &#9633; usage - directs the server to generate message describing supported
##   arguments and then exit

## Configuration File

## At startup the utserver process looks for a configuration file which allows the
## behavior of the product to be customized by changing the values of certain
## settings. The format of this file is as follows:

## &#9633; each setting is on a separate line;
## &#9633; each line consists of colon-separated name of the setting and its
##   value;
## &#9633; any line whose first non-whitespace character is # is a comment.

## For example, a file that sets two values and includes one comment might look
## like:

# This is a comment
## dir_temp_files: temp
## preferred_interface: eth0

## For a complete list of application settings, see Application Settings.

## Environment

## When the utserver process creates files intended for end users, such as torrent
## data files, it uses the value of the file mode creation mask to specify access
## to these files. For more information, run man umask on a Linux command line.
## The value of the file mode creation mask is not considered when creating files
## not intended for use by users, such as settings files.

## Ensure the locale used by the utserver process supports your preferred
## character set or that of your users. By default, without explicit
## configuration, utserver running on some Linux devices will support only the
## 8-bit C/POSIX locales. Choose a locale that supports UTF-8 or other character
## set that is more likely to support the torrents created by the international
## community of BitTorrent users. Set the LANG environment variable to your choice
## of locale, and ensure your desired locale is supported on the computer running
## utserver.

## Application Settings

## Settings fall into two categories:

## &#9633; internal settings, whose values can only be set in the utserver.conf
##   file;
## &#9633; regular settings, whose values can be set in the utserver.conf file or
##   the /api/app-settings-set RPC API call.

## A setting can be of one of three types:

## &#9633; string
## &#9633; integer
## &#9633; Boolean value (1 for true and 0 for false)

##
## Internal Settings
##

# bind_ip:
## bind_ip (string):
## IP address to use for socket connections. If not provided, a default IP
## address will be used. We do not recommend changing this value.

# ut_webui_port:
## ut_webui_port (integer):
## Default value: 8080. Port number where the utserver process accepts HTTP
## RPC API calls to support the µTorrent-compatible HTTP interface. If the
## utserver process also serves HTML files (see webui_server_files setting),
## also the port of HTTP server.

# token_auth_enable:
## token_auth_enable (boolean)
## Default value: true. If true, the µTorrent HTTP interface defends against
## cross-site request forgeries by requiring that a short-lived token be
## obtained from the µTorrent HTTP interface and included at the beginning of
## the parameter list of any request made to that interface. If false, the
## µTorrent HTTP interface will not be protected in this manner.

dir_active: /home/<USERNAME>/Bittorrent/
## dir_active (string):
## Default value: "./". Directory in which currently downloaded data is saved.
## Can be an absolute path or a relative path. If it is a relative path, the
## value is relative to dir_root or the current working directory if dir_root
## is not defined or an empty string. It is recommended that this directory be
## hidden from users (i.e. not exported through Samba).

dir_completed: /home/<USERNAME>/Bittorrent/Completed/
## dir_completed (string):
## Default value: "". Directory where completed downloads are stored. If the
## value is an empty string, the value of dir_active is used. This value must
## represent a path that is accessible to users (e.g. exported through Samba).
## It also has to be on the same volume as dir_active.

# dir_download:
## dir_download (string):
## Default value: "". Optional directory where completed downloads can be
## stored, instead of in dir_completed. If no value is specified for this
## setting, the value of dir_completed is used. The value must represent a
## path that is accessible to users (e.g. exported through Samba).

## This option can be specified multiple times in the file - once for each
## directory to be designated as such. This option can be used when adding
## torrents via the µTorrent HTTP interface, not via the SDK interface.

## Use the action list-dirs to obtain a list of download directories from the
## µTorrent HTTP interface. Use the option download_dir to specify which of
## these directories to use when adding a torrent by URL or file through the
## µTorrent HTTP interface; specify the one-based index of the entry of
## interest. The index of each entry will be in order in which each entry
## appears in utserver.conf, starting with 1 for the first entry, 2 for the
## second entry, and so on. 0 indicates the default download directory should
## be used.

## The value of this setting will be applied every time the utserver process
## starts or the configuration file is reloaded.

dir_torrent_files: /home/<USERNAME>/.utserver/dottorrent/
## dir_torrent_files (string):
## Default value: "". Directory where torrent files are stored. If the empty
## string, the value of dir_active is used. It is recommended that this
## directory be hidden from users (i.e. not exported through Samba).

# dir_temp_files:
## dir_temp_files (string):
## Default value: "". Directory where temporary files are stored. If the empty
## string, the value of dir_active is used. It is recommended that this
## directory be hidden from users (i.e. not exported through Samba). Also,
## using a separate directory just for temporary files allows for deleting the
## files in this directory on boot and/or periodically. The utserver process
## creates temporary files with a .utt extension - if a value for this setting
## is specified, the utserver process will delete all files with that
## extension in that directory at process startup. This setting applies only
## to POSIX systems. The value should specify a directory, not a symbolic link
## to a directory.

dir_autoload: /home/<USERNAME>/.utserver/dottorrent/autoload/
## dir_autoload (string):
## Default value: "". Directory where torrent files will be recognized and
## auto-loaded. If the empty string, auto-load is disabled.

# dir_autoload_delete:
## dir_autoload_delete (boolean):
## Default value: false. If true, torrent files in the autoload directory will
## be deleted after being loaded, else they will be renamed with an extension
## of .loaded. The dir_autoload setting must be specified for this setting to
## have an effect.

dir_request: /home/<USERNAME>/.utserver/request/
## dir_request (string):
## Default value: "". Directory where maintenance request files will be
## recognized, loaded, and deleted. If the empty string, maintenance request
## handling is disabled.

## Software running on the server can create the following files in this
## directory in order to request the following maintenance procedures.

## If the file c.utmr is created in or moved into this directory, the
## credentials necessary to access the µTorrent HTTP interface will be reset
## to username admin and a blank password.

## If the file wipl.utmr is created in or moved into this directory, the IP
## restriction list that limits the IPs that can use the µTorrent HTTP
## interface is cleared, so that there will be no restrictions on IP address.

## These maintenance operations provide a way to help a user who has either
## entered new credentials and then forgotten them, or who has entered an IP
## range in the restricted list and can no longer access the µTorrent HTTP
## interface as a result.

## If the file rcf.utmr is created in or moved into this directory, the server
## will reload the configuration file. If you always use this method to
## request a configuration file reload, you can safely change the value of
## this setting while the server is running.

## The server will also reload the configuration file if you send a hangup
## signal to the server; however, a race condition may occur if you send a
## hangup signal to the server in order to change the value of this setting.
## You should either only use the file system interface for requesting
## configuration file reloads, or you should not change the value of this
## setting in the configuration file before sending a hangup signal to the
## server.

## If the file sp.utmr is created in or moved into this directory, the
## utserver process will exit after performing normal shutdown processing such
## as saving settings files and torrent resume data. This can be useful for
## changing configuration file settings that are best applied on process
## startup.

## Ensure the access permissions for this directory permit only appropriate
## authenticated users and/or processes to create, list, and delete files.
## This directory should be unavailable to other users and processes (i.e.,
## not exported through Samba). If you want a requesting process to create
## maintenance request files in this directory, ensure that both the
## requesting process and the utserver process have rights to this directory.

## The value of this setting will be applied every time the utserver process
## starts or the configuration file is reloaded.

# upnp:
## upnp (boolean):
## Default value: true. If true, UPNP functionality for mapping ports is used
## by utserver. We recommend setting this value to true.

# natpmp:
## natpmp (boolean):
## If true, NAT-PMP functionality for mapping ports is used by utserver.
## Default value: true. We recommend setting this value to true.

# lsd:
## lsd (boolean):
## Default value: true. If true, Local Service Discovery is enabled. We
## recommend setting this value to true.

# dht:
## dht (boolean):
## Default value: true. If true, Distributed Hash Table extension is enabled.
## We recommend setting this value to true.

# pex:
## pex (boolean):
## Default value: true. If true, Peer Exchange extension is enabled. We
## recommend setting this value to true.

# rate_limit_local_peers:
## rate_limit_local_peers (boolean):
## Default value: false. If true, rate limiting also applies to communications
## with peers in the local subnet. We recommend setting this value to false.

# dir_root:
## dir_root (string):
## Default value: "". If not empty, dir_active, dir_completed, and
## dir_torrent_files are relative to this directory.

# disk_cache_max_size:
## disk_cache_max_size (integer):
## Default value: 0. Maximum amount of memory used by each of the read, write,
## and piece caches. Value is in megabytes. If 0, accepts the server's default
## choices on selecting sizes of disk caches. Maximum value is 512.

## The value of this setting will be applied every time the utserver process
## starts or the configuration file is reloaded.

# write_coalesce_max_size:
## write_coalesce_max_size (integer):
## Default value: 0. The maximum amount of contiguous torrent file data that
## will be held before writing it to disk. Adjusting this value may affect
## disk write efficiency on some systems. Value is in megabytes. Maximum value
## is 32. If 0, accepts the server's default (2) on selecting sizes of writes
## to coalesce. If -1, disables write caching.

## The value of this setting will be applied every time the utserver process
## starts or the configuration file is reloaded.

# progressive_piece_span:
## progressive_piece_span (integer):
## Default value: 0. The maximum amount of readahead for torrents that are
## being downloaded in the more sequential progressive mode (as opposed to the
## more random rarest-first mode). Value is in megabytes. Maximum value is
## 1024. If 0, accepts the server's default (80) on maximum readahead on
## progressive downloads. If -1, disables progressive piece picker.

## The value of this setting will be applied every time the utserver process
## starts or the configuration file is reloaded.

# preferred_interface:
## preferred_interface (string):
## Default value: "". If defined, name of network interface to be preferred
## when attempting to search among network interfaces for an external IP and
## hardware address. If empty string, preferred interface is ignored.

## You need to provide a value for this setting if either 1) the toolchain for
## your computer does not supply ifaddrs.h, or 2) you want the utserver
## process to choose a different interface than it would choose on its own.
## You should set a value for this setting if you see an incorrect port
## mapping on a UPnP router for the subnet to which the device belongs (the IP
## address of the device will not appear in the port mapping requested by the
## utserver process - instead, the IP address associated with the mapping will
## be 0.0.0.0 with a device having a toolchain that does not include
## ifaddrs.h, or some other IP address with a device having a toolchain that
## includes ipaddrs.h).

## The value of this setting will be applied every time the utserver process
## starts or the configuration file is reloaded.

admin_name: <USERNAME>
## admin_name (string):
## Default value: "admin". If defined, name that must be supplied (along with
## the password) when authenticating to the server via the HTTP interface.
## This allows the administrator to define an initial non-default value for
## this name. This value will not be applied from utserver.conf if
## settings.dat already exists.

admin_password: <PASSWORD>
## admin_password (string):
## Default value: "". If defined, password that must be supplied (along with
## the name) when authenticating to the server via the HTTP interface. This
## allows the administrator to define an initial non-default value for this
## password. This value will not be applied from utserver.conf if settings.dat
## already exists.

# localhost_authentication:
## localhost_authentication (boolean):
## Default value: true. If false, HTTP requests originating from the local
## host will not be required to include administrative user name and password.
## Disabling authentication of requests originating on the local host may be
## useful on computers where there are no other users or processes that
## shouldn't be prevented from accessing the HTTP interface. Disabling
## authentication presents a security risk on those computers that support
## untrusted users or allow third-party applications to be installed and run
## outside the control of the administrator.

## The value of this setting will be applied every time the utserver process
## starts or the configuration file is reloaded.

# logmask:
## logmask (integer):
## Default value: 0. A mask whose bits when set allow certain categories of
## log messages to be generated. The value of this setting will be applied
## every time the utserver process starts or the configuration file is
## reloaded.

## The bits (0 - 31) in the value of this setting correspond to a set of
## internal events and subsystems. The usage of these bits may change without
## advance notice in a future release.

## &#9633; 3 - send have
## &#9633; 6 - hole punch
## &#9633; 7 - got bad piece request
## &#9633; 8 - trace
## &#9633; 9 - piece picker
## &#9633; 10 - got bad cancel
## &#9633; 11 - got bad unchoke
## &#9633; 12 - got bad piece
## &#9633; 13 - rss
## &#9633; 14 - rss error
## &#9633; 15 - got have
## &#9633; 16 - got bad have
## &#9633; 17 - error
## &#9633; 18 - aggregated
## &#9633; 19 - disconnect
## &#9633; 20 - out connect
## &#9633; 21 - in connect
## &#9633; 22 - UPnP
## &#9633; 23 - UPnP error
## &#9633; 24 - NATPMP
## &#9633; 25 - NATPMP error
## &#9633; 26 - metadata finish
## &#9633; 27 - web UI
## &#9633; 28 - got bad reject
## &#9633; 29 - pex
## &#9633; 30 - peer messages
## &#9633; 31 - blocked connect

ut_webui_dir: /opt/utorrent-server-alpha-v3_3/
## ut_webui_dir (string):
## Directory where the web UI file archive webui.zip is stored, or which
## contains a webui subdirectory within which the unarchived web UI files are
## stored. It can be an absolute path or set relative to the current
## directory. It is recommended that this directory be hidden from users (i.e.
## not exported through Samba). Default value: "" (to use the same directory
## as settings.dat and other settings files).

## The value of this setting will be applied every time the utserver process
## starts or the configuration file is reloaded.

# finish_cmd:
## finish_cmd (string), state_cmd (string):
## If defined, finish_cmd is a command that will be executed upon completion
## of each torrent, and state_cmd is a command that will be executed when a
## torrent changes state. Default value: "" (no command is run for the event
## (s) associated with that setting).

## The command is run asynchronously, so that a lengthy or hung process will
## not block the server. The server creates a new process group for the
## command, so that the server does not need to wait for it, and so the kernel
## process table does not fill up with zombie processes. The command is run as
## the same user that runs the server process.

## The server permits substitutions in the command text as follows:

## %F
## Name of downloaded data file (for single-file torrents)
## %D
## directory where torrent data files are saved
## %N
## torrent title
## %S
## torrent state
## %P
## previous state of torrent
## %L
## label associated with torrent
## %T
## tracker
## %M
## status message
## %I
## hex-encoded info-hash

## State (%S) and previous state (%P) are integers that have the following
## values:

## &#9633; 1 (error)
## &#9633; 2 (checked)
## &#9633; 3 (paused)
## &#9633; 4 (super seeding)
## &#9633; 5 (seeding)
## &#9633; 6 (downloading)
## &#9633; 7 (super seeding (forced))
## &#9633; 8 (seeding (forced))
## &#9633; 9 (downloading (forced))
## &#9633; 10 (queued seed)
## &#9633; 11 (finished)
## &#9633; 12 (queued)
## &#9633; 13 (stopped)

# uconnect_enable:
## uconnect_enable (boolean):
## Default value: false. If true, the values of uconnect_username and
## uconnect_password are provided when authenticating to µTorrent Remote. The
## value of this setting will be applied every time the utserver process
## starts or the configuration file is reloaded. This value is always applied
## from utserver.conf; it is not saved in settings.dat.

# uconnect_username:
## uconnect_username (string):
## Default value: "". If defined, name that must be supplied (along with the
## password) when authenticating to µTorrent Remote. The value of this setting
## will be applied every time the utserver process starts or the configuration
## file is reloaded. This value is always applied from utserver.conf; it is
## not saved in settings.dat.

# uconnect_password:
## uconnect_password (string):
## Default value: "". If defined, password that must be supplied (along with
## the name) when authenticating to µTorrent Remote. The value of this setting
## will be applied every time the utserver process starts or the configuration
## file is reloaded. This value is always applied from utserver.conf; it is
## not saved in settings.dat.

low_cpu: 1
## low_cpu (boolean):
## Default value: false. If true, a short sleep occurs during the process of
## handling network traffic, so that network traffic handling presents less of
## a load on the CPU. This value will not be applied from utserver.conf if
## settings.dat already exists.

# sequential_download:
## sequential_download (boolean):
## Default value: false. If true, torrent pieces are requested in order. This
## is used to help prevent disk congestion on slow disks such as USB drives.
## This value is always applied from utserver.conf.

# compact_allocation:
## compact_allocation (boolean):
## Default value: false. If true, torrent pieces are appended to the end of
## the files as they come in and rearranged dynamically. The downside of
## compact allocation is currently it does not work with mutlifile torrents
## where we are selectively downloading only some of the files. This value is
## always applied from utserver.conf.

prealloc_space: 1
## prealloc_space (boolean):
## Default value: false. If true, disk space for a torrent is allocated before
## the first piece is written to disk. Note that this is not compatible with
## and overrides compact_allocation. This value is always applied from
## utserver.conf.

# minimize_kernel_caching:
## minimize_kernel_caching (boolean):
## Default value: false. If true all disk handles opened on a win32/vfat
## filesystem will be flagged for synchronous I/O when they are opened and
## torrents downloaded to these filesystems will have compact allocation
## enabled. This will minimize a hang that can occur when the kernel disk
## cache becomes full when writing to USB devices formatted as win32/vfat.
## This value is always applied from utserver.conf.

# all_writes_sync:
## all_writes_sync (boolean):
## Default value: false. If true, all writable disk handles opened are flagged
## for synchronous I/O disk space for a torrent is allocated before the first
## piece is written to disk. This value is always applied from utserver.conf.

randomize_bind_port: 1
## randomize_bind_port (boolean):
## Default value: false. If true, a random port will be chosen as the peer
## port at startup, even if the user has chosen a different peer port during
## the previous run of the product. If false, the value of the bind_port
## setting will apply. This value is applied from utserver.conf only at
## program start.

# token_auth_filter:
## token_auth_filter (string):
## Default value: all. Determines which set of IP addresses will require the
## use of token authentication. Value considered only when the
## token_auth_enable setting has a value of true. The value remote will
## require token authentication from remote IP addresses. The value all will
## require token authentication from all IP addresses. This value is applied
## from utserver.conf only at program start.

# encrypt_buffer_size:
## encrypt_buffer_size (integer):
## Default value: 102400. Minimum value: 4096. For builds including OpenSSL,
## determines the size of the encryption buffer allocated for SSL
## communications. This value is applied from utserver.conf only at program
## start.

##
## Regular Settings
##

# bind_port:
## bind_port (integer):
## Default value: 6881. Port used for BitTorrent protocol. This can be any
## value in the range 1025-65000.

max_ul_rate: 5000
## max_ul_rate (integer):
## Default value: -1. Maximum total upload rate in kilobytes per second. -1
## means unlimited. We recommend setting it to -1.

max_ul_rate_seed: 500
## max_ul_rate_seed (integer):
## Default value: -1. Maximum per-torrent upload rate when seeding, in
## kilobytes per second. -1 means unlimited. We recommend setting it to -1.

# conns_per_torrent:
## conns_per_torrent (integer):
## Default value: 50. Maximum number of connections for a given torrent.

# max_total_connections:
## max_total_connections (integer):
## Default value: 200. Maximum number of connection opened at the same time.

# auto_bandwidth_management:
## auto_bandwidth_management (boolean):
## Default value: true. If true, upload bandwidth is automatically throttled
## in order to not impact other applications using TCP/IP.

# max_dl_rate:
## max_dl_rate (integer):
## Default value: -1. Maximum total download rate in kilobytes per second. -1
## means unlimited. We recommend setting it to -1.

seed_ratio: 200
## seed_ratio (integer):
## Default value: 0. Seed ratio in percent (%) (e.g. 100 means 100%). If not
## 0, seeding will stop after reaching this upload/download ratio.

# seed_time:
## seed_time (integer):
## Default value: 0. Time after which seeding will stop, in seconds. 0 means
## seeding won't stop.

##
## Reloadable Settings
##

## Many of these settings are only read from the configuration file when the
## µTorrent settings file settings.dat does not already exist in the settings
## directory. Once settings.dat exists, the values specified in the configuration
## file for these settings will be ignored, and the values stored in settings.dat
## will be used. For other settings, the server will load the values from the
## configuration file every time the program starts or receives a request to
## reload the configuration file.

## The settings for which the values are always applied from the configuration
## file when the file is read by the server include:

## &#8226; dir_download
## &#8226; dir_request
## &#8226; disk_cache_max_size
## &#8226; localhost_authentication
## &#8226; logmask
## &#8226; preferred_interface
## &#8226; progressive_piece_span
## &#8226; uconnect_enable
## &#8226; uconnect_password
## &#8226; uconnect_username
## &#8226; ut_webui_dir
## &#8226; write_coalesce_max_size
```

Note: Obviously, this large config file would quite easily render down to:
```
# Quick and dirty configuration file
# for Linux uTorrent server:
# utserver.conf
dir_active: /home/<USERNAME>/Bittorrent/
dir_completed: /home/<USERNAME>/Bittorrent/Completed/
dir_torrent_files: /home/<USERNAME>/utserver/dottorrent/
dir_autoload: /home/<USERNAME>/utserver/dottorrent/autoload/
dir_request: /home/<USERNAME>/utserver/request/
admin_name: <USERNAME>
admin_password: <PASSWORD>
ut_webui_dir: /opt/utorrent-server-alpha-v3_3/
low_cpu: 1
prealloc_space: 1
randomize_bind_port: 1
max_ul_rate: 5000
max_ul_rate_seed: 500
seed_ratio: 200
```

However, well commented config files are *always* recommended because they can be a lifesaver!
[For the full, unadulterated template configuration file, just follow this link.]("http://forum.utorrent.com/topic/73370-sample-utserverconfig-file/#entry497396")

Now, create a symbolic link so that you can run the torrent server from the command line:

```
sudo ln -s /opt/utorrent-server-alpha-v3_3/utserver /usr/bin/utserver
```

**At this point, test it out to see if it works:**

NOTE:

```
utserver -usage
```
```
Locale en_GB.UTF-8
330B (30470) 2014-01-14 09:10:15 -0800
Usage:  utserver -settingspath -logfile -configfile -pidfile -daemon -usage
	settingspath - location of settings directory
	logfile - location and name of log file
	configfile - location and name of configuration file
	pidfile - location and name of file to contain process ID
	daemon - run process as a daemon
	usage - print this message and exit
```

That&#8217;s it. Now you can start the utorrent server by using the following command in a terminal:

```
utserver -settingspath /home/<USERNAME>/.utserver/ -configfile /home/<USERNAME>/.utserver/utserver.conf -logfile /home/<USERNAME>/.utserver/utserver.log -pidfile /home/<USERNAME>/.utserver/utserver.pid -daemon
```

To access utorrent server, open a browser and navigate to:

[http://localhost:8080/gui/](http://localhost:8080/gui/)

[SIZE=5]How To Start µTorrent Server as a Service[/SIZE]

[http://www.webupd8.org/2011/02/start-utorrent-server-as-daemon-with.html](http://www.webupd8.org/2011/02/start-utorrent-server-as-daemon-with.html)

Create an init script:

```
sudo vim /etc/init/utserver.conf
```
```
#/etc/init/utserver.conf
 description "µTorrent Server"
 author "Rich.T."
 # Start the service after everything loaded
 start on (local-filesystems and started dbus and stopped udevtrigger)
 stop on runlevel [016]
 # Automatically restart service
 respawn
 respawn limit 99 5
 script
    
     # Run utserver
     su <USERNAME> -c "utserver -settingspath /home/<USERNAME>/.utserver/ -configfile /home/<USERNAME>/.utserver/utserver.conf -logfile /home/<USERNAME>/.utserver/utserver.log -pidfile /home/<USERNAME>/.utserver/utserver.pid -daemon"
 end script
```
 
To test it:

Restart your computer and test it in your browser!

[SIZE=5]How To Create a Desktop / Unity Launcher Shortcut for Starting and Stopping µTorrent Server[/SIZE]

[B]If you are on a desktop PC and don't want utserver running as a background task, but instead
want to use it like a desktop application, follow these instructions:[/B]
(Note: (Double-)Click the icon once to start utorrent and a second time to shut it down.)

Firstly, use your archive manager to extract the icon called "ut.png" from "/opt/utorrent-server-alpha-v3_3/webui.zip" to the folder "/opt/utorrent-server-alpha-v3_3/" (just drag'n'drop). This will give you both a pretty icon and a professional looking desktop notification.

Create a startup/notifier script for utserver in the same folder:

```
vim /opt/utorrent-server-alpha-v3_3/utserver.sh
```
```
#!/bin/sh

if pidof utserver >/dev/null 2>&1
	then
		 zenity --question \
				--no-wrap \
				--title="µTorrent Server" \
				--window-icon="/opt/utorrent-server-alpha-v3_3/ut.png" \
				--text="<big><b>Are you sure you want to shut down µTorrent Server?</b></big>\n\nPlease ensure that all running torrents are stopped before confirming.\n\n<b>Thank You. &#9786;</b>"
				case $? in
				0)	notify-send -i /opt/utorrent-server-alpha-v3_3/ut.png 'µTorrent Server' 'Now Shutting Down' &
					killall utserver
					while [ "$(pidof utserver)" ]; do
					sleep 1
					done
					sleep 3
					killall notify-osd
					notify-send -i /opt/utorrent-server-alpha-v3_3/ut.png 'µTorrent Server' 'Now Shut Down' &
					exit 0
				;;
				1)	exit 0
				;;
                esac
        else
                notify-send -i /opt/utorrent-server-alpha-v3_3/ut.png 'µTorrent Server' 'Now Starting' &
                utserver -settingspath /home/richard/.utserver/ -configfile /home/richard/.utserver/utserver.conf -logfile /home/richard/.utserver/utserver.log -pidfile /home/richard/.utserver/utserver.pid -daemon
                while [ -z "$(pidof utserver)" ]; do
                sleep 1
                done 
                sleep 1
                killall notify-osd
                sleep 1
                notify-send -i /opt/utorrent-server-alpha-v3_3/ut.png 'Launching Browser' &
                sleep 1
                xdg-open http://localhost:8080/gui &
                exit 0
    fi

notify-send -i /opt/utorrent-server-alpha-v3_3/ut.png 'µTorrent Server' 'Error' &

exit 0
```

Make the script executable:

```
chmod a+x /opt/utorrent-server-alpha-v3_3/utserver.sh
```

Now create a .desktop file for the shortcut:

```
vim /home/<USERNAME>/.local/share/applications/utserver.desktop
```
```
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Name=µTorrent Server
Icon=/opt/utorrent-server-alpha-v3_3/ut.png
Path=/opt/utorrent-server-alpha-v3_3/
Exec=/opt/utorrent-server-alpha-v3_3/utserver.sh
StartupNotify=false
StartupWMClass=utserver
OnlyShowIn=Unity;
X-UnityGenerated=true

```
Make the shortcut executable:

```
chmod a+x /home/<USERNAME>/.local/share/applications/utserver.desktop
```

**Done! The shortcut should now be accessable through the Menu/HUD and pinnable to the Launcher.**

I hope that this helps people out and makes the usage of µTorrent Server more user-friendly for day to day use.

Rich.

---

### Post by Rich.T. on 2014-11-19
Reserved.

---

