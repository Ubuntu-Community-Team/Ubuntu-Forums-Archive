---
title: "Dear Ubuntu'ers. Please learn from my mistake."
date: 2010-01-22
forum: The Cafe
---

### Post by Roasted on 2010-01-22
I have 2 drives in my PC. One for OS + Data, and the other for simply a backup of my data. Yesterday my main drive detected errors and was failing. I took the data on my backup drive, backed it up elsewhere, and decided I was going to try Clonezilla to suck up the image on the failing hard drive and plop it on my secondary drive.

While on a LiveCD sorting through my data, I didn't have access to get into my Ubuntu partition. So. I did it.

sudo chmod -R 777 disk

NOOOOOOOOOOOOOOOO. Did I really do -R? Really? 

That said, it recursively changed ALL permissions in my drive to be maxed out. Recovering all permissions from something like this is just... impossible. But hey - I had my home directory backed up, so that's good at least. So I sucked up the Vista install as an image, plopped it on my drive (Thank God, Vista alone takes forever to install, and all of the games I have make it worse). Then just installed Ubuntu the manual way (only took 11 minutes. Wow?) and pulled my data back.

This is coming from an Ubuntu user of nearly 5 years. Don't be an idiot. Don't type faster than you can think. Read the commands prior to issuing them. Had I not done that, I could have taken the entire contents of the failing drive, plopped them on the spare drive, and been okay. But instead I could only save Vista and reinstalled Ubuntu.

---

### Post by earthpigg on 2010-01-22
> While on a LiveCD sorting through my data, I didn't have access to get into my Ubuntu partition. So. I did it.

sudo chmod -R 777 disk

any reason you didn't go ahead and 'sudo nautilus'? or 'sudo su' if working at the command line.

---

### Post by NoaHall on 2010-01-22
Don't worry. I don't need to learn from your mistakes. Because I wouldn't make them anyway :)

---

### Post by Roasted on 2010-01-22
> **earthpigg said:**
> any reason you didn't go ahead and 'sudo nautilus'? or 'sudo su' if working at the command line.

Some of us aren't that slick. :P

---

### Post by juancarlospaco on 2010-01-22
**[/Fixed]("apt:/nautilus-gksu")**

---

### Post by dragos240 on 2010-01-22
> **Roasted said:**
> I have 2 drives in my PC. One for OS + Data, and the other for simply a backup of my data. Yesterday my main drive detected errors and was failing. I took the data on my backup drive, backed it up elsewhere, and decided I was going to try Clonezilla to suck up the image on the failing hard drive and plop it on my secondary drive.

While on a LiveCD sorting through my data, I didn't have access to get into my Ubuntu partition. So. I did it.

sudo chmod -R 777 disk

NOOOOOOOOOOOOOOOO. Did I really do -R? Really? 

That said, it recursively changed ALL permissions in my drive to be maxed out. Recovering all permissions from something like this is just... impossible. But hey - I had my home directory backed up, so that's good at least. So I sucked up the Vista install as an image, plopped it on my drive (Thank God, Vista alone takes forever to install, and all of the games I have make it worse). Then just installed Ubuntu the manual way (only took 11 minutes. Wow?) and pulled my data back.

This is coming from an Ubuntu user of nearly 5 years. Don't be an idiot. Don't type faster than you can think. Read the commands prior to issuing them. Had I not done that, I could have taken the entire contents of the failing drive, plopped them on the spare drive, and been okay. But instead I could only save Vista and reinstalled Ubuntu.

I've actually done EXACTLY what you did.

---

### Post by k64 on 2010-01-22
I once did this on my Linpus installation. Never going back.
 
First of all, when I tried to run Sudo, here's what happened:
 
```
sudo: must be setuid root
```.
 
That said, this is a very insecure change. It can cause irreparable damage to the entire filesystem.

---

### Post by earthpigg on 2010-01-22
im kind of a fan of pcmanfm.

pic related.

[IMG]http://tombuntu.com/wp-content/uploads/2008/05/pcmanfm2.jpg[/IMG]

and after you hit ok, it gives you the option to apply changes recursively. ive only used that once, but iirc it asks for an additional confirmation if you select yes.

i couldn't think of a more noob-friendly or pleasant to use way to do that stuff.

---

### Post by xir_ on 2010-01-22
> **dragos240 said:**
> I've actually done EXACTLY what you did.

yep me too, third time i ever booted linux on my laptop and was playing round with commands, i thought, hey i wonder what would happen....

---

### Post by JohnFH on 2010-01-22
I did it intentionally on a test system to see what would happen.  I thought something along the lines of "Well, what harm can it do anyway?".  Actually, quite a lot!

---

### Post by Swagman on 2010-01-22
I did that on an Amiga once upon a long ago.

I was in the shell in a directory and I issued a delete #? all command expecting to delete everything in ***THAT*** directory.

It's a horrible feeling when.. as the text whizzes past you start noticing things like

Libs/.....
Devs/....

What ?

**NoOOOOOOOOOOOOOOOooooooooooooooooooooooo**

Too late.

---

### Post by Roasted on 2010-01-22
My problem was I was previously using the chmod -R command for other stuff. So I was still in that mindset and typed it without thinking. Hit enter and blam. Effed.

I understand completely what I did wrong. It's something I was previously good about watching. I was just frustrated cause I had so many things going on that weren't working right and blam. This bit me in the rear end.

---

### Post by fromthehill on 2010-01-22
> **Roasted said:**
> 
sudo chmod -R 777 disk


I'm not the only one who did this :D

---

### Post by Roasted on 2010-01-22
I was also kind of absent minded, because I kept thinking - livecd - when I reboot everything goes back to the way it was - etc - so I wasn't on guard for the commands I was issuing.

At least I did chmod -R and not rm -rf. At least my data was still -there- instead of buhbyes.

PS - DO NOT EVER USE RM -RF.

---

### Post by nothingspecial on 2010-01-22
No offence, but over the years, browsing the forums I have been compiling a list named "Really stupid things you can do when running linux".

This is going in it.

My favourite is still 
```

find ./ -type f -exec mv '{}' ./ \;
```

issued from the home directory.

---

### Post by init1 on 2010-01-22
> **Roasted said:**
> I have 2 drives in my PC. One for OS + Data, and the other for simply a backup of my data. Yesterday my main drive detected errors and was failing. I took the data on my backup drive, backed it up elsewhere, and decided I was going to try Clonezilla to suck up the image on the failing hard drive and plop it on my secondary drive.

While on a LiveCD sorting through my data, I didn't have access to get into my Ubuntu partition. So. I did it.

sudo chmod -R 777 disk

NOOOOOOOOOOOOOOOO. Did I really do -R? Really? 

That said, it recursively changed ALL permissions in my drive to be maxed out. Recovering all permissions from something like this is just... impossible. But hey - I had my home directory backed up, so that's good at least. So I sucked up the Vista install as an image, plopped it on my drive (Thank God, Vista alone takes forever to install, and all of the games I have make it worse). Then just installed Ubuntu the manual way (only took 11 minutes. Wow?) and pulled my data back.

This is coming from an Ubuntu user of nearly 5 years. Don't be an idiot. Don't type faster than you can think. Read the commands prior to issuing them. Had I not done that, I could have taken the entire contents of the failing drive, plopped them on the spare drive, and been okay. But instead I could only save Vista and reinstalled Ubuntu.
I've done that before. I had to reinstall, but I didn't loose anything.

---

### Post by Roasted on 2010-01-22
> **nothingspecial said:**
> No offence, but over the years, browsing the forums I have been compiling a list named "Really stupid things you can do when running linux".

This is going in it.

My favourite is still 
```

find ./ -type f -exec mv '{}' ./ \;
```

issued from the home directory.

No offense? Pfft. I encourage it. If people can learn from my stupid mistakes the world will be a better place. :guitar:

And uh... what's that command... do?

---

### Post by fromthehill on 2010-01-22
> **nothingspecial said:**
> 
```

find ./ -type f -exec mv '{}' ./ \;
```

when you find ./ (current folder?) rename it to '\'?
just guessing :P

---

### Post by schauerlich on 2010-01-22
> **Roasted said:**
> And uh... what's that command... do?

It takes every file in every subdirectory of the current directory, and moves it up to the current directory, overwriting wherever there's naming conflicts.

---

### Post by k64 on 2010-01-22
What I did was something similar:

```
sudo chmod -R 777 /
```

This is basically the same thing.

---

### Post by xuCGC002 on 2010-01-22
> **juancarlospaco said:**
> **[/Fixed]("apt:/nautilus-gksu")**

I hate that package. It replaces writing 6 letters and a space, or moreso creating a launcher which takes about 10 seconds.

---

### Post by HermanAB on 2010-01-23
Hmm, I once accidentally deleted a whole operational web server.  It took me about 4 hours to restore it from backup.  It kinda drove the point home about having backups, but since then I review my commands before pressing Enter.

---

### Post by jpmelos on 2010-01-23
Hello. I'm really sorry if this is stupid, but I don't get it. If you do sudo chmod -R 777 disk, it just changes permission of everything to be readable, writable and executable by everyone, right? You don't lose any data. Right so far?

So, to recover from that, all you need to do is change the permission of everything to 744 and should be fine? I mean, everything that is in your home folder will be only executable and writable by you, everything outside, only by the root... Then, you change everything inside /bin, /usr/bin and all other bin folders to 755. Problem solved?

I mean, I don't really know if this would work out. Why wouldn't it? Again, sorry if this is stupid...

---

### Post by k64 on 2010-01-23
> **jpmelos said:**
> Hello. I'm really sorry if this is stupid, but I don't get it. If you do sudo chmod -R 777 disk, it just changes permission of everything to be readable, writable and executable by everyone, right? You don't lose any data. Right so far?

So, to recover from that, all you need to do is change the permission of everything to 744 and should be fine? I mean, everything that is in your home folder will be only executable and writable by you, everything outside, only by the root... Then, you change everything inside /bin, /usr/bin and all other bin folders to 755. Problem solved?

I mean, I don't really know if this would work out. Why wouldn't it? Again, sorry if this is stupid...

"sudo chmod -R 777 /" will do the same thing.

---

### Post by cguy on 2010-01-23
And why doesn't the system work if everything is 777?

What are the exact errors?

---

### Post by llawwehttam on 2010-01-23
> **dragos240 said:**
> I've actually done EXACTLY what you did.

Guilty too. This was a while ago though.

---

### Post by jwbrase on 2010-01-23
> **cguy said:**
> And why doesn't the system work if everything is 777?

What are the exact errors?

Apparently there are files like ~/.dmrc that the system will gag on if they don't have certain permissions. Even without that, everything being 777 is very insecure.

---

### Post by jpmelos on 2010-01-23
> **k64 said:**
> "sudo chmod -R 777 /" will do the same thing.

Sorry, didn't get it.

---

### Post by Roasted on 2010-01-24
> **jpmelos said:**
> Hello. I'm really sorry if this is stupid, but I don't get it. If you do sudo chmod -R 777 disk, it just changes permission of everything to be readable, writable and executable by everyone, right? You don't lose any data. Right so far?

So, to recover from that, all you need to do is change the permission of everything to 744 and should be fine? I mean, everything that is in your home folder will be only executable and writable by you, everything outside, only by the root... Then, you change everything inside /bin, /usr/bin and all other bin folders to 755. Problem solved?

I mean, I don't really know if this would work out. Why wouldn't it? Again, sorry if this is stupid...

Sorry? Stupid? Dude. This is where you SHOULD ask questions, as opposed to trying them out and seeing unfortunate results. :P 

Understand that "disk" was exclusive to my situation. You see... I was booted up to a LiveCD trying to recover the data. My actual hard drive was auto-mounted to /media/disk of the LiveCD. So if I went to /media, I would see the folder labeled "disk". This is how Ubuntu just assigns generic names to volumes that don't have a label. So when I did chmod -R 777 disk, I essentially changed the permissions of my ENTIRE internal drive. Every file. Every folder. Every. Damn. Thing. Was changed... all because of the -R.

If I said sudo chmod 777 disk, it would have changed the permissions to the parent folder "disk."

Since I used sudo chmod -R 777 disk, the -R takes the permissions to everything inside (and including) the parent folder itself. That's where I screwed up.

So if you go to your computer and do sudo chmod -R 777 /  , you'll essentially do the same thing. / is root. Root is "everything." Because I wasn't booted in Ubuntu (and to a LiveCD), I didn't have "root" because my disk wasn't the one I was booted into - and the Ubuntu LiveCD just placed it as /media/disk.

Make sense? If not feel free to ask. ;)

---

### Post by lisati on 2010-01-24
> **NoaHall said:**
> Don't worry. I don't need to learn from your mistakes. Because I wouldn't make them anyway :)
So you DID learn from it, or was it from experience?
> **Swagman said:**
> I did that on an Amiga once upon a long ago.

I was in the shell in a directory and I issued a delete #? all command expecting to delete everything in ***THAT*** directory.

It's a horrible feeling when.. as the text whizzes past you start noticing things like

Libs/.....
Devs/....

What ?

**NoOOOOOOOOOOOOOOOooooooooooooooooooooooo**

Too late.

Or cleaning up an MS-DOS machine, and idly putting in something like ```
format C:
```

Another one is trying to set up a machine to install Win98 from the hard disk instead of CD (it can be done) so clean out C: with the above same format command, copying the relevant portions of the Win98 installation CD to a folder, put the format command in again without thinking, going to run the setup, and then :confused: :D

---

### Post by nothingspecial on 2010-01-25
> **schauerlich said:**
> It takes every file in every subdirectory of the current directory, and moves it up to the current directory, overwriting wherever there's naming conflicts.

So, say you have a music collection of 10,000 mp3s in ~/music all aranged neatly in Artist/Album foders, you now have 10,000 mp3 files in home and nothing in your Artist/Album folders. And each mp3 is listed in alphabetical order so you would have to know exactly which song is on which album and put them back one by one. And if you have live albums or compilations with different versions of tracks but with the same name, you only have one version now.

Same goes for photos, videos etc.

Of course if you issued that from / who knows what fun would occur.

---

### Post by schauerlich on 2010-01-25
> **nothingspecial said:**
> Of course if you issued that from / who knows what fun would occur.

Let's try it!

---

### Post by lisati on 2010-01-25
> **nothingspecial said:**
> So, say you have a music collection of 10,000 mp3s in ~/music all aranged neatly in Artist/Album foders, you now have 10,000 mp3 files in home and nothing in your Artist/Album folders. And each mp3 is listed in alphabetical order so you would have to know exactly which song is on which album and put them back one by one. And if you have live albums or compilations with different versions of tracks but with the same name, you only have one version now.

Same goes for photos, videos etc.

Of course if you issued that from / who knows what fun would occur.

The same can be said for video and pictures.....care is needed to make sure that everything is stored where it should be.

---

### Post by nothingspecial on 2010-01-25
> **lisati said:**
> The same can be said for video and pictures.....care is needed to make sure that everything is stored where it should be.

In that case it should be **V**ideos and **P**ictures.

I changed the directories in my home along time ago to lowercase, and exchanged Pictures for photos.


> Let's try it!

I have a testing partition on one of my boxes, but it is also testing other stuff, maybe one day.....
.... I`ll post the results............if I do.

---

### Post by Roasted on 2010-01-25
If you're going to try something like that, it'd be fun to Clonezilla the image prior. So when you nuke it, plop the image back, and try other fun malicious commands that you would otherwise never dream of using.

Yay for linux experiments on spare computers!

---

### Post by nothingspecial on 2010-01-25
> **schauerlich said:**
> Let's try it!

Oh yes!

That really does ***** things up. Here`s my / on my teasting partition as far as gnome terminal will let you scroll up.

```
i915_gem_request
i915_gem_seqno
i915_ringbuffer_data
i915_ringbuffer_info
iad_bFirstInterface
iad_bFunctionClass
iad_bFunctionProtocol
iad_bFunctionSubClass
iad_bInterfaceCount
ibm.conf
ibmtts.conf
ibm-wireless
ibm-wireless.sh
ibus
icverrors
id
id.ctb
idle_timeout
idProduct
idVendor
ifalias
ifindex
iflink
ifupdown.sh
ignore_ce
ignore_nice_load
imaging_capabilities.xml
im-multipress.conf
inactive_ms
index
indicator-applet.desktop
inetd.conf
init_pin_configs
initramfs
initramfs.conf
initrd.img
initrd.img.old
init_verbs
inode_goal
inode_readahead_blks
input.conf
inputrc
inquiry_cache
insserv
insserv.conf
intel-hda-powersave.conf
intel-sata-powermgmt.conf
interface
interfaces
interval
iocounterbits
iodone_cnt
ioerr_cnt
iorequest_cnt
iostats
ipa.ctb
ip-down
ip-up
ipv6-down
ipv6-up
irq
isql
issue
issue.net
is.ttb
it.ttb
ivona.conf
ja.ctb
jade.cat
jockey-common
jockey-gtk.desktop
kannada.tti
kde
kdeglobals
kerberosclient
kernel-img.conf
kernel_max
kerneloops
kerneloops.conf
kexec_crash_loaded
kexec_loaded
key
keyboard-setup
keyidx
keylen
keypad.ktb
kha.ttb
killprocs
kn.ttb
ko.ctb
ko-g1.ctb
ko-g2.ctb
KOI8RXTerm
kok.ttb
kru.ttb
l2cap
laptop.ktb
laptop-mode
laptop-mode.conf
larch
last_seq_ctrl
Lat15-VGA16.psf.gz
latency
latex-xft-fonts.hints
launcher-10.rc
launcher-7.rc
launcher-9.rc
launchpad-integration
lcd-brightness.conf
ldap.conf
ld.so.cache
ld.so.conf
led
legal
lenovo-touchpad
leo.conf
letters-cyrillic.tti
letters-latin.cti
letters-latin-dot8.tti
letters-latin.tti
level
lexmark.conf
lftp.conf
lib
libao.conf
libasound2.conf
libc.conf
libnet.cfg
libpisock9.conf
lidbtn
lid.sh
lifetime_write_kbytes
likewise
lilypond
limits.conf
link
link_mode
lisp
list
llia_phon-generic.conf
local_cpulist
local_cpus
locale
locale.alias
local.ini
localstore.rdf
localtime
loc-cset.data
lockbtn.sh
logical_block_size
login
login.defs
logprof.conf
logrotate
logrotate.conf
long_retry_limit
lost+found
lsb-base-logging.sh
lsb-release
ltrace.conf
lt.ttb
lv.ttb
lzma
lzop
ma1509.conf
macaddress
machine.config
magic
magic.mime
mailbtn.sh
mailcap
mailcap.order
mailman
main.conf
malayalam.tti
manage_start_stop
man-db
man.local
manpath.config
manufacturer
matsushita.conf
max_age
maxchild
max_hw_sectors_kb
max_ratectrl_rateidx
max_ratio
max_sectors_kb
max_state
max_user_freq
mb_group_prealloc
mb_max_to_scan
mb_min_to_scan
mb_order2_req
mb_stats
mb_stream_req
MCFG
mcrypt
mdns
mdoc.local
media
mediabtn.sh
menurc
metacity-common.cat
meta-release
mfg
mg.ctb
mg.ttb
microtek2.conf
microtek.conf
mime.types
mimeTypes.rdf
minicom
minimum_io_size
min_ratio
misc
mi.ttb
mke2fs.conf
mlocate
ml.ttb
mni.ttb
mnt
modalias
mode
model
modelname
model_name
modes
module-init-tools.conf
modules
moduli
monarch_timeout
monodevelop
motd.tail
Motif.ad
mountall.conf
mountall-net.conf
mountall-reboot.conf
mountall-shell.conf
mpd
mpd.conf
mr.ttb
msc
msi_bus
mtab
mtools.conf
mt.ttb
mtu
multicast
multicast_received_frame_count
multicast_transmitted_frame_count
multiple_retry_count
mun.ctb
mun.ttb
mustek.conf
mustek_pp.conf
mustek_usb.conf
mutebtn.sh
mwr.ttb
my.cnf
mysql
nabcc.cti
name
nameservice
namespace.conf
namespace.init
nanorc
nec.conf
net.conf
netscsid.conf
ne.ttb
net-tools
network.conf
networking
networking.conf
network-interface.conf
network-manager.conf
NetworkManager.conf
networks
newprinternotification.conf
new.ttb
newusers
nextbtn.sh
nis
nl_BE.ttb
nl.ctb
nl_NL.ttb
nl.ttb
nm-applet.conf
nm-applet.desktop
nm-avahi-autoipd.conf
nm-dhcp-client.conf
nm-dispatcher.conf
nm-system-settings.conf
noack
no-generic.ttb
noise
nomerges
none
no-oub.ttb
notes
no.ttb
nr_requests
nsswitch.conf
ntpdate
number
number_of_sets
numbers-dot6.tti
numbers-dot8.tti
numbers-french.tti
numbers-nemeth.tti
num_ps_buf_frames
nvidia
nvidia-common
nvram
nwc.ttb
nwid
ny.ctb
oauth_urls
offline
ondemand
online
ooffice.sh
opasswd
openssh-server
openssl.cnf
operstate
opt
optimal_io_size
options
orbit2
org.blueman.Mechanism.conf
org.debian.apt.conf
org.freedesktop.DeviceKit.Disks.conf
org.freedesktop.DeviceKit.Power.conf
org.freedesktop.ModemManager.conf
org.freedesktop.PolicyKit1.conf
org.freedesktop.PolicyKit.conf
org.freedesktop.SystemToolsBackends.conf
org.gnome.ClockApplet.Mechanism.conf
org.gnome.CPUFreqSelector.conf
org.gnome.GConf.Defaults.conf
oriya.tti
or.ttb
other
overcommit
p4
packages-whitelist
pam.conf
pam_env.conf
pan
panasonic-lockbtn
panels.xml
pango.conf
pap
papersize
pap-secrets
partition
passwd
passwd-
path
pa.ttb
pcmciautils
pcm_class
pdftops.conf
perl
persist
persistent
php5
phys
physical_block_size
physical_line_partition
physical_package_id
pid
pie.conf
pi.ttb
pixma.conf
playbtn.sh
pl.ttb
plustek.conf
plustek_pp.conf
pm-utils
pnm2ppa.conf
policykit
PolicyKit.conf
polkit
polkit-1
polkit-gnome-authentication-agent-1.desktop
pon
pools
popularity-contest
popularity-contest.conf
possible
povray
power
powerbtn
powerbtn.sh
powersave_bias
power.sh
ppp
pppd-dns
pppoe_on_boot
preferences.fdi
prefs.js
present
prev_bssid
prevbtn.sh
print-applet.desktop
printk_formats
priority
private-files
private-files-strict
proc
proc_name
procps.conf
product
product_name
product_serial
product_uuid
product_version
profile
profiles
profiling
prot_capabilities
protection_type
prot_guard_type
proto
protocol
protocols
provider
ps-cset-enc.data
ps-menurc
psprint.conf
pt.ctb
pt.ttb
pulseaudio
punctuation-alternate.tti
punctuation-basic.tti
python
qcam.conf
qdbus
qemu
quantum
queue_depth
queues
queue_type
quirks
quota-tools
range
rarian-compat.xml
rate
raw.convs
raw.types
rc
rc.conf
rc.local
rcS
rcS.conf
rc_stats
rc-sysinit.conf
rdesktop
read_ahead_kb
README
README.blacklist
reboot
received_fragment_count
redglass.theme
rel
related_cpus
release-upgrades
remap
removable
replays
reserve_percpu
reset
resetafter
resolution
resolv.conf
resource
resource0
resource1
resource2
resource2_wc
resource3
resource4
resource_alignment
resources
resume
resync_time
retries
retry_count
rev
revision_id
rfc3442-classless-routes
rfcomm
rfcomm.conf
rfcomm_dlc
rgb.txt
ri
ricoh.conf
rmt
ro
rom
root
root_id
root_path_cost
root_port
rotate
rotatescreen.sh
rotational
ro.ttb
rpc
rq_affinity
rsync
rsyslog
rsyslog.conf
rsyslog-kmsg.conf
rt_dsfield
rt_protos
rt_realms
rts8891.conf
rt_scopes
rts_threshold
rt_tables
ruby
ru.ttb
rx_bytes
rx_compressed
rx_crc_errors
rx_dropped
rx_errors
rx_fifo_errors
rx_frame_errors
rx_length_errors
rx_missed_errors
rx_over_errors
rx_packets
rx_spec
s9036.conf
samba
sampling_rate
sampling_rate_max
sampling_rate_min
saned
saned.conf
sa.ttb
sat.ttb
sbcl
sbin
sbin.dhclient3
scaling_available_frequencies
scaling_available_governors
scaling_cur_freq
scaling_driver
scaling_governor
scaling_max_freq
scaling_min_freq
scaling_setspeed
sceptre.conf
sched_features
sched-mc-power-savings.conf
sched_smt_power_savings
scheduler
sci
sci_not
sco
screenblank.sh
screen-cleanup
screenrc
scroll
scsi_level
sd.ttb
seahorse-daemon.desktop
secring.gpg
securetty
selinux
sendsigs
sensors.conf
sepermit.conf
serial
serial_number
services
session.conf
sessionrc
session_write_kbytes
set
set_event
settings.map
settings.menu
severities-coverage
severity.db
sgml-data.cat
sgml-data.cat.old
sgml-data.xml
sgml-data.xml.old
sg_tablesize
shadow
shadow-
shared_cpu_list
shared_cpu_map
sharp.conf
shells
shlibs.default
shlibs.override
short_retry_limit
si.ctb
since_epoch
single
sitecopy
sitecustomize.py
size
skeleton
sk.ttb
sleepbtn
sleepbtn.sh
sleep.sh
SLIC
slice_async
slice_async_rq
slice_idle
slice_sync
sm3840.conf
smb.conf
smbpass
snapscan.conf
snd
sniff_max_interval
sniff_min_interval
snmp.conf
snownews
sofficerc
soffice.sh
softraw
softrepeat
sony-mute
sony-sleep
sony-volume-down
sony-volume-up
sources.list
sp15c.conf
spaces.tti
speechd.conf
speech-dispatcher
speechd-user-port.sh
speed
srv
SSDT1
SSDT2
SSDT3
SSDT4
SSDT5
SSDT6
SSDT7
ssh
ssh_config
sshd
sshd_config
ssh_host_dsa_key
ssh_host_dsa_key.pub
ssh_host_rsa_key
ssh_host_rsa_key.pub
ssid_len
ssl_certs
ssl-cert-snakeoil.key
ssl-cert-snakeoil.pem
ssl_keys
st400.conf
standard
start
start_lba
start-stop-programs.conf
stat
state
stats
status
statusrc
stop-bootlogd
stop-bootlogd-single
stopbtn.sh
stp_state
stride
stv680.conf
su
subdomain.conf
subsystem_device
subsystem_id
subsystem_vendor
_subversion
sudo
sudoers
supported_mode
supports_autosuspend
sv-1989.ttb
sv-1996.ttb
svk
svn-repositories
sv.ttb
sw
sw.ctb
swift-generic.conf
sw.ttb
syncdaemon.conf
sys
sysctl.conf
system.conf
system-greprefs.js
system.pa
systray-4.rc
sys_vendor
tamarack.conf
tamil.tti
ta.ttb
tcn_timer
TCPA
technology
teco1.conf
teco2.conf
teco3.conf
telugu.tti
temp
temp1_crit
temp1_input
templaterc
terminal-blanking.conf
test.conf
te.ttb
th.ctb
thinkpad-cmos
thinkpad-stretchortouchpad.sh
thread_siblings
thread_siblings_list
throttle.conf
thttpd
thttpd.conf
th-xim
time
time.conf
time_in_state
timeout
timezone
Tk.ad
TMOR
tmp
tmpfs
tolerant
topology_change
topology_change_detected
topology_change_timer
tosh-battery
tosh-hibernate
tosh-ibutton
tosh-lock
tosh-mail
tosh-media
tosh-next
tosh-play
tosh-prev
tosh-stop
tosh-wireless
tosh-wireless.sh
tosh-www
total_ps_buffered
total_trans
trace
trace_pipe
trace_pipe_raw
transmitted_fragment_count
transmitted_frame_count
trans_table
trigger
trip_point_0_temp
trip_point_0_type
trip_point_1_temp
trip_point_1_type
tr.ttb
trustdb.gpg
trusted.gpg
trusted.gpg~
ts.conf
tsf
ttf-dejavu-core.hints
ttf-freefont.hints
ttf-indic-fonts-core.hints
ttf-kacst.hints
ttf-lao.hints
ttf-liberation.hints
ttf-mscorefonts-installer.hints
ttf-thai-tlwg.hints
ttf-unfonts-core.hints
ttf-vlgothic.hints
ttf-wqy-zenhei.hints
tty1.conf
tty2.conf
tty3.conf
tty4.conf
tty5.conf
tty6.conf
tx_aborted_errors
tx_bytes
tx_carrier_errors
tx_compressed
tx_dropped
tx_errors
tx_fifo_errors
tx_heartbeat_errors
tx_packets
tx_queue_len
tx_rx_count
tx_spec
tx_window_errors
type
u12.conf
ubufox.js
ubuntu
ubuntu-browsers
ubuntu.conf
ubuntu-console-browsers
ubuntu-console-email
ubuntu-email
ubuntu-gnome-terminal
ubuntu-konsole
ubuntuone
ubuntuone-client-crashdb.conf
UbuntuOne-Go_Daddy_CA.pem
UbuntuOne-Go_Daddy_Class_2_CA.pem
ubuntu-xterm
uca.xml
ucf.conf
udev.conf
udev-finish.conf
udevmonitor.conf
udevtrigger.conf
uevent_helper
uevent_seqnum
ufw
ufw.conf
umax1220u.conf
umax.conf
umax_pp.conf
umountfs
umountnfs.sh
umountroot
unace
unattended-upgrades
unchecked_isa_dma
Uni1-VGA16.psf.gz
uniq
unique_id
unitrc
unload_heads
unrar
updatedb.conf
update-initramfs.conf
update-notifier.desktop
upstart
Upstart.conf
upstart-udev-bridge.conf
up_threshold
urandom
urbnum
ureadahead.conf
ureadahead-other.conf
usage
usb-autosuspend.conf
useradd
userChrome-example.css
userContent-example.css
user-dirs.conf
user-dirs.defaults
user-dirs-update-gtk.desktop
user-download
user-mail
user-manpages
user_pin_configs
user-tmp
user-write
usplash
usplash.conf
usr
usr.bin.evince
usr.bin.firefox-3.5
usr.sbin.cupsd
usr.sbin.tcpdump
UXTerm
v4l.conf
var
vendor
vendor_id
vendor_name
version
video
videobtn
videobtn.sh
video-out.conf
Viewres
vimrc
vimrc.tiny
vino-server.desktop
virtual_size
vi.ttb
vm
vma
vmcoreinfo
vmlinuz
vmlinuz.old
vncviewer
voldownbtn.sh
voltage_min_design
voltage_now
volupbtn.sh
waiting
wakealarm
wakeup
ways_of_associativity
webbtn.sh
web.config
web-data
wep_iv
wgetrc
whiteglass.theme
wildmidi.cfg
winbind
wireless-ipw-power.conf
wireless-iwl-power.conf
wireless-tools
wMaxPacketSize
wodim.conf
wpa_action
wpa-ifupdown
wpa_supplicant
wpa_supplicant.conf
wutmp
X
x11-common
xad
Xaw.ad
XCalc
XCalc-color
XClipboard
XClock
XClock-color
XConsole
Xditview
Xditview-chrtr
Xedit
Xedit-color
xenc-cset.data
xerox_mfp.conf
xfce4-keyboard-shortcuts.xml
xfce4-menu-5.rc
xfce4-session.xml
xfce4-settings-helper-autostart.desktop
xfce4-tips-autostart.desktop
xfce4-volumed.desktop
xfce-applications.menu
xfconf-migration-4.6.desktop
Xfd
xfonts-100dpi.alias
xfonts-75dpi.alias
xfonts-base.alias
XFontSel
xfonts-mathml.hints
xfonts-mathml.scale
xfonts-scalable.scale
Xft.xrdb
Xgc
xinitrc
XLoad
XLogo
XLogo-color
Xmag
Xman
Xmessage
Xmessage-color
xml-core.cat
xml-core.xml
xml-core.xml.old
XMore
xorg-server.conf
XScreenSaver-gl
XScreenSaver-nogl
xserverrc
Xsession
Xsession.options
xsettings.xml
XSm
xsplash.conf
XTerm
XTerm-color
x-ttcidfont-conf.conf
x-ttcidfont-conf.conf2
Xvidtune
XvMCConfig
Xwrapper.config
zh-tw.ctb
zh-tw-polyphone.cti
zh-tw-ucb.ctb
zsh_command_not_found
zu.ctb
```

By the way, I don`t have many personal files on my testing partition.

The scariest bit was that I became (something like) "I have no name!@rob-netbook"

I tried to copy the output, but although the splash screen came up, I had no gedit, nano or open office writer.

Yep, if you want to toast your system, issue that command as root from /.

I just did that so you don`t have to ;)

---

### Post by nothingspecial on 2010-01-25
Smell, I had loads of beta software running on that partition.....

....oh well, I have always been easily led.

---

### Post by schauerlich on 2010-01-25
> **nothingspecial said:**
> Smell, I had loads of beta software running on that partition.....

....oh well, I have always been easily led.

Haha :) Thanks for biting the bullet!

---

### Post by nothingspecial on 2010-01-25
> **schauerlich said:**
> Haha :) Thanks for biting the bullet!

That`s what a testing partition is for :P

---

### Post by MooPi on 2010-03-01
I've done something similar but different and wonder if I'll have issues. Non bootable drive, just storage, ```
sudo chown username -R diskname
``` Problems ?

---

### Post by MasterNetra on 2010-03-01
> **MooPi said:**
> I've done something similar but different and wonder if I'll have issues. Non bootable drive, just storage, ```
sudo chown username -R diskname
``` Problems ?

I would think as -R would remove the ability to read the file(s) and/or folder(s) specified. 

Also don't "sudo chown username /" I once did that. Had some problems to put it mildly.

---

