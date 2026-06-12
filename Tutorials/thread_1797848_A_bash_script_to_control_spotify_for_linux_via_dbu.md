---
title: "A bash script to control spotify for linux via dbus"
date: 2011-07-05
forum: Tutorials
---

### Post by azzid on 2011-07-05
I wrote a script some time ago to be able to control the mediaplayer spotify from a script. I've found it really useful, for example when I wanted to map my keyboard media keys to work with spotify.

I thought someone else would appreciate the script aswell, so here it is:

```
#!/bin/bash

# Collect DBUS_SESSION_BUS_ADDRESS from running process
function set_dbus_adress
{
	USER=$1
	PROCESS=$2
	PID=`pgrep -o -u $USER $PROCESS`
	ENVIRON=/proc/$PID/environ

	if [ -e $ENVIRON ]
	 then
	export `grep -z DBUS_SESSION_BUS_ADDRESS $ENVIRON`
	 else
	echo "Unable to set DBUS_SESSION_BUS_ADDRESS."
	exit 1
	fi
}

function spotify_cmd
{
	dbus-send --print-reply --dest=org.mpris.MediaPlayer2.spotify /org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.$1 1> /dev/null
}

function spotify_query
{
	qdbus org.mpris.MediaPlayer2.spotify /org/mpris/MediaPlayer2 org.freedesktop.DBus.Properties.Get org.mpris.MediaPlayer2.Player PlaybackStatus
}

function quit_message
{
	echo "Usage: `basename $0` {play|pause|playpause|next|previous|stop|playstatus|<spotify URI>}"
	exit 1
}

# Count arguments, must be 1
if [ "$#" -ne "1" ]
then
        echo -e "You must supply exactly one argument!\n"
	quit_message
fi

# Check if DBUS_SESSION is set
if [ -z $DBUS_SESSION_BUS_ADDRESS ] 
	 then
	#echo "DBUS_SESSION_BUS_ADDRESS not set. Guessing."
	set_dbus_adress `whoami` spotify
fi

case "$1" in
        play)
		spotify_cmd Play
                ;;
        pause)
		spotify_cmd Pause
                ;;
        playpause)
		spotify_cmd PlayPause
                ;;
        next)
		spotify_cmd Next
                ;;
        previous)
		spotify_cmd Previous
                ;;
        stop)
		spotify_cmd Stop
                ;;
        spotify:user:*)
		spotify_cmd "OpenUri string:$1"
		spotify_cmd Play
                ;;
        spotify:*:*)
		spotify_cmd "OpenUri string:$1"
                ;;
	playstatus)
		spotify_query
		;;
        *)
                echo -e "Bad argument.\n"
                quit_message
                ;;
esac

exit 0

```

Enjoy! And if you do like it, please drop a line here so that I'll know about it. ;)

**Edit/FYI:** They (spotify developers) changed something with the latest release breaking the 'playstatus' command, but hopefully they fix it with the next release.

---

### Post by jachy on 2011-07-16
I like it... a lot :)

Now I can easily change songs from my Thinkpad's with Fn and arrow keys. Thanks!\\:D/

---

### Post by penguininja on 2011-07-18
Just what I was looking for; works perfectly.  Thanks!!

---

### Post by repunante on 2011-08-09
Sorry to bother but I don't have much experience in this.
Do I just execute the script?
Do I have to edit the script according to the multimedia keys of my keyboard? In which part?

Thanks.

---

### Post by azzid on 2011-08-10
> **repunante said:**
> Sorry to bother but I don't have much experience in this.
Do I just execute the script?
Do I have to edit the script according to the multimedia keys of my keyboard? In which part?

Thanks.

You can try the script in a bash terminal, you'll have to supply an argument to describe if you want the script to press 'play', 'pause' etc.

When you understand how to use the script you can use the keyboard shortcut setting GUI in the menu of ubuntu to map different keys to different executions of the script.

You should not have to alter the script, just supply it with different arguments.

---

### Post by repunante on 2011-08-10
> **azzid said:**
> You can try the script in a bash terminal, you'll have to supply an argument to describe if you want the script to press 'play', 'pause' etc.

When you understand how to use the script you can use the keyboard shortcut setting GUI in the menu of ubuntu to map different keys to different executions of the script.

You should not have to alter the script, just supply it with different arguments.


I don't have a clue about writing/editing scripts, I will make some research on my own and I will try to make it work.
Thanks for the help.

---

### Post by nuclear_eclipse on 2011-08-10
[https://github.com/jreese/spotify-gnome](https://github.com/jreese/spotify-gnome)

---

### Post by repunante on 2011-08-10
> **nuclear_eclipse said:**
> [https://github.com/jreese/spotify-gnome](https://github.com/jreese/spotify-gnome)


Thanks!

---

### Post by domolicious on 2011-09-21
Thanks alot!!

> **jachy said:**
> I like it... a lot :)

Now I can easily change songs from my Thinkpad's with Fn and arrow keys. Thanks!\\:D/

Amen!! :D

---

### Post by dioxip on 2011-10-12
Wow! Thanks alot, just what I've been searching for!

---

### Post by azzid on 2011-12-03
As an exercise I translated the script from bash to perl.

It is somewhat nicer in perl imho, so here is that version aswell:
```
#!/usr/bin/perl

use 5.010;
use strict;
use warnings;
use File::Basename;
use Net::DBus;

  # Figure out some dbus stuff
  unless ( defined $ENV{'DBUS_SESSION_BUS_ADDRESS'} ) { 
	&set_DBUS_SESSION_BUS_ADDRESS;
	#die "Don't know which dbus to attach to.\nMake sure environment variable DBUS_SESSION_BUS_ADDRESS is set.";
	}
  #my $bus = 		Net::DBus->find;
  my $bus = 		Net::DBus->session;
  my $spotify =		$bus->get_service("org.mpris.MediaPlayer2.spotify");
  my $player =		$spotify->get_object("/org/mpris/MediaPlayer2", "org.mpris.MediaPlayer2.Player");
  my $application =	$spotify->get_object("/org/mpris/MediaPlayer2", "org.mpris.MediaPlayer2");
  my $getorset =	$spotify->get_object("/org/mpris/MediaPlayer2", "org.freedesktop.DBus.Properties");

# Handle command line argument
if (scalar @ARGV == 0) { &print_help; }
given ($ARGV[0]) {
#	when ('play') { 	$player->Play(); }		#Does not work for some reason.
	when ('pause') { 	$player->Pause(); }
	when ('playpause') { 	$player->PlayPause(); }
	when ('next') { 	$player->Next(); }
	when ('previous') { 	$player->Previous(); }
	when ('stop') { 	$player->Stop(); }
	when ('playstatus') { print $getorset->Get("org.mpris.MediaPlayer2.Player", "PlaybackStatus") . "\n"; }
	when (m/\bspotify:(artist|album|track):[0-9a-zA-z]{22}\b/) { $player->OpenUri($_); }
	when ('metadata-debug') { &print_debug_metadata; }
	default { &print_help; }
}
	

# Print the help text
sub print_help {
	print "USAGE: " . basename($0) . " {pause|playpause|next|previous|stop|playstatus|metadata-debug|<spotify URI>}\n\n";
	print "\t" . "pause"		. "\t\t"	. "Causes spotify to pause current playback."		. "\n";
	print "\t" . "playpause"	. "\t"		. "Causes spotify to pause or play current playback."	. "\n";
	print "\t" . "next"		. "\t\t"	. "Goes to next song."					. "\n";
	print "\t" . "previous"		. "\t"		. "Goes to previous song."				. "\n";
	print "\t" . "stop"		. "\t\t"	. "Stops playback."					. "\n";
	print "\t" . "playstatus"	. "\t"		. "Prints current playstatus (Playing/Paused)."		. "\n";
	print "\t" . "<spotify URI>"	. "\t"		. "Starts playing supplied URI."			. "\n";
	print "\t" . "metadata-debug"	. "\t"		. "Shows available data on currently playing song."	. "\n";
	print "\t" 			. "\t\t"	. "Fairly unformatted, thus \"debug\" data."		. "\n";
	print 													  "\n";
	print "EXAMPLES:\t"	. basename($0) . " playpause" 							. "\n";
	print "\t\t" 		. basename($0) . " spotify:track:5XXAq1r5r73ZyBS0XAiGw0"			. "\n";
	
	exit;
}

# Print some raw metadata
sub print_debug_metadata {
	# Dereference the metadata hashref by copying it to a local hash
	my %metadata = %{ $getorset->Get("org.mpris.MediaPlayer2.Player", "Metadata") };

	# Print all metadata
	print "Now Playing:\n";
	for (keys %metadata) {
		print $_ . ":\t" . $metadata{$_} . "\n" unless ($_ eq 'xesam:artist');
	}

	# Dereference the artist arrayref by copying it to local array
	my @artistarray = @{ $metadata{'xesam:artist'} };

	# Print all artists.
	foreach my $artist (@artistarray) {
		print "artist: \t" . $artist . "\n";
	}
}

sub set_DBUS_SESSION_BUS_ADDRESS {
	my $curruser	= `whoami`; chomp $curruser;
	my $procname	= 'spotify';
	my $pid		= `pgrep -o -u $curruser $procname`; chomp $pid;
	my $environ	= '/proc/' . $pid . '/environ';
	my $dbussession = `grep -z DBUS_SESSION_BUS_ADDRESS $environ`; $dbussession =~ s/^DBUS_SESSION_BUS_ADDRESS=//;

	$ENV{'DBUS_SESSION_BUS_ADDRESS'} = $dbussession;
}

```

---

### Post by fysicalplant on 2011-12-06
[<duplicate removed>]("http://www.mabishu.com/blog/2010/11/15/playing-with-d-bus-interface-of-spotify-for-linux/")

---

### Post by fysicalplant on 2011-12-06
[http://www.mabishu.com/blog/2010/11/...ify-for-linux/]("http://www.mabishu.com/blog/2010/11/15/playing-with-d-bus-interface-of-spotify-for-linux/")

use keyboard shortcuts (System Settings>Keyboard>Shortcuts>Custom Shortcuts) or compiz command shortcuts to create shortcuts for the lines here. just change the end for PlayPause, Next, and Previous

IMPORTANT: Before creating shortcuts using the System Settings, be sure to check Sound and Media and disable those shortcuts first (click and use Backspace to disable a shortcut).  If you happen to have created the shortcut before disabling the old one, simply reassign the old one, then disable using backspace, then re-enable the new one.  Not sure if this is necessary using Compiz.

---

### Post by azzid on 2011-12-06
> **fysicalplant said:**
> [http://www.mabishu.com/blog/2010/11/...ify-for-linux/]("http://www.mabishu.com/blog/2010/11/15/playing-with-d-bus-interface-of-spotify-for-linux/")

use compiz command shortcuts with the lines here. just change the end for playpause next and previous

I'd like to point out that the script can be used for other things than just binding your keyboard media keys.

Controlling spotify through ssh for instance...

---

### Post by wapko on 2012-03-10
a bit late to the party. but just wanted to say thank you!. been looking for something like this.

---

### Post by lazypoet on 2012-06-06
Just a note... If anybody gets the following error...

```
Can't locate Net/DBus.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.14.2 /usr/local/share/perl/5.14.2 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.14 /usr/share/perl/5.14 /usr/local/lib/site_perl .) at /home/kerrick/scripts/spotify-dbus.pl line 7.
BEGIN failed--compilation aborted at /home/kerrick/scripts/spotify-dbus.pl line 7.
```

...then you need to install libnet-dbus-perl and it'll work fine. This can be done by entering the following command as root or sudo:

```
sudo apt-get install libnet-dbus-perl
```

Thanks to OP for the fantastic script!

---

### Post by nem75 on 2012-07-11
@azzid: thanks a lot, great script, well done!

---

### Post by e04mk on 2012-09-21
To be able to add playlists via this script add the following line at line 87.
```
when (m/\bspotify:user:[0-9a-zA-z]*:playlist:[0-9a-zA-z]{22}\b/) { $player->OpenUri($_); }
```

Thanks for the script, it's exactly what you need and nothing more.

---

### Post by azzid on 2012-09-21
> **e04mk said:**
> To be able to add playlists via this script add the following line at line 87.
```
when (m/\bspotify:user:[0-9a-zA-z]*:playlist:[0-9a-zA-z]{22}\b/) { $player->OpenUri($_); }
```

Thanks for the script, it's exactly what you need and nothing more.

Nice! Thanks! I added something similar at home.
Never did find that "golden regexp" to describe all possible spotify uri:s.

---

### Post by forumdoctor on 2012-12-18
This didnt work for me. Have they changed anything?
Does Gnome-Spotify work in Unity?

---

### Post by azzid on 2012-12-18
> **forumdoctor said:**
> This didnt work for me. Have they changed anything?
Does Gnome-Spotify work in Unity?

I've kept using the scripts, and they still work (for me).

I just realized that I'm still using the bash-script in my keybindings, but both scripts work when I test them on the command line:

```
$ ./spotify-dbus.pl playpause
$ ./spotify-remote.sh playpause
```

My spotify versions:
```
$ dpkg-query --list | grep -i spotify
ii  spotify-client                                1:0.8.4.103.g9cb177b.260-1                      Spotify desktop client
ii  spotify-client-qt                             1:0.8.4.103.g9cb177b.260-1                      Transitional package for spotify-client

```

My install is a vanilla ubuntu 10.04 upgraded to 12.04.

---

