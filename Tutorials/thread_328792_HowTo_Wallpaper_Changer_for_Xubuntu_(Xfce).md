---
title: "HowTo: Wallpaper Changer for Xubuntu (Xfce)"
date: 2006-12-31
forum: Tutorials
---

### Post by hyper_ch on 2006-12-31
Hiya

I have switched to Xubuntu a few months ago coming from Kubuntu. I liked there the (already available) option of setting up a list of image files and have them randomly displayed. This was one of the things I have missed so far in Xfce.

As former Windows user I have aquired quite a large number of wallpapers (thx goes to HTTrack for downloading over 18k wallpapers...) and I like to have them displayed on the background. That's more or the less the only major change I do on a theme (if you can call that a change...)

Anyway, thx to TheSheep from the #xubuntu channel on irc.freenode.org (he's a really helpful guy and has helped me countless time) I can provide you with this small howto.

**(1) Build your list of images**
- Right-click on your desktop
- Select "Desktop settings"
- Make sure that "Allow Xfce to manage the desktop" and "Show Image" boxes are checked (they are by default)
- Click then on "New list"
- Add the image files by clicking on the "+"
- Once you are done, save the list
- You are back in the previous screen and your newly created list should be selected in the "File" input box
- Then close that interface

**(2) Creating Cronjob for Wallpaper Changer functionality**
- Open a terminal
- If you already have a "cron-command" file for your user, open that one in a text editor if not execute this command: *nano cron.txt*
- Enter the following two lines to the cron file:
> 
# Reload Background Image
0,5,10,15,20,25,30,35,40,45,50,55 * * * * killall -USR1 xfdesktop

This will change the image every 5 minutes. You can also change the behaviour. Please refer here: [Cron HowTo]("https://help.ubuntu.com/community/CronHowto")
- Exit nano by pressing *ctrl-x*
- Press [y] to save the file

**(3) Adding the Cronjob for Wallpapcher Changer**
- Before you overwrite any existing user cronjobs please execute this command:
> 
crontab -l

If nothing is returned then it's fine to add you wallpaper changer script!
- Add the cron.txt file that we created under section (2) by issuing the following command in the shell:
> 
crontab cron.txt

- Enter now again *crontab -l* and you should have this output:
> 
hyper@xubi:~$ crontab -l
# Reload Background Image
0,5,10,15,20,25,30,35,40,45,50,55 * * * * killall -USR1 xfdesktop


**(4) That's it**
- Get some coffee or whatever and enjoy your desktop bakground wallpaper changer :)

---

### Post by Tails on 2006-12-31
ah, nice one, I will try it later night.. this is 1 hell of the hack I want to have in xfce.. :D

---

### Post by eteran on 2007-01-07
Thanks for the hint, works out great.

Just as a little addition, the crontab line could be also written as:
```
*/5 * * * * killall -USR1 xfdesktop
```
to change the background every 5 minutes

---

### Post by eteran on 2007-01-14
somebody might find this script useful.
you will need to have at least php4-cli installed to run it.

[php]
#!/usr/bin/env php
<?php

/**
 * xfce4-background-changer
 *
 * a bit of automating for the xfce4 desktop
 *
 * it recreates the background list automaticly as I found the gui
 * not comfortable enough and "reloads" afterwards the desktop causing a
 * new background picture being randomly displayed
 * you can put it in your crontab to change the background every
 * now and then (man crontab)
 * f.e. "* * * * * ~/scripts/xfce4-background-changer.php"
 * or you might place a desktop starter to change the background
 * everytime you activate the starter
 *
 * PHP version 4 and 5
 *
 * LICENSE:
 * This program is free software; you can redistribute it and/or modify
 * it under the terms of the GNU General Public License as published by
 * the Free Software Foundation; either version 2 of the License, or
 * (at your option) any later version.
 *
 * This program is distributed in the hope that it will be useful,
 * but WITHOUT ANY WARRANTY; without even the implied warranty of
 * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 * GNU General Public License for more details.
 *
 * You should have received a copy of the GNU General Public License
 * along with this program; if not, write to the Free Software
 * Foundation, Inc., 51 Franklin St, Fifth Floor, Boston, MA  02110-1301  USA
 * 
 * @author    David Uhlig <david.uhlig@googlemail.com>
 * @copyright 2007 David Uhlig <david.uhlig@googlemail.com>
 * @license   http://www.gnu.org/licenses/gpl.txt GNU GPL
 * @version   1.0  
 */
 
// {{{ settings

/**
 * home
 */
define('HOME', $_ENV['HOME']);

/**
 * directories with wallpapers, or wallpaper files
 * use absolute path, seperate by comma
 * !!! no closing slash for directorys
 * !!! directories will _not_ be walked through recursive 
 */
define('BACKGROUND_DIR', HOME . '/.wallpaper');

/**
 * absolute path to your background list as choosen via 
 * Applications / Settings / Background -> Picture -> File 
 */
define('BACKGROUND_LIST', HOME . '/.config/xfce4/desktop/hintergrundbilder.list');

// }}}

// {{{ functions

/**
 * rewriteBackgroundList
 */
function rewriteBackgroundList()
{
	$res = fopen(BACKGROUND_LIST, "w");
	fwrite($res, "# xfce backdrop list\n");
	
	if ($res === false)
	{
		return;
	}
	
	$aryBackgroundDir = split(",", BACKGROUND_DIR);	
	
	foreach ($aryBackgroundDir as $strBackgroundDir)
	{
		if (is_dir($strBackgroundDir))
		{
			$aryDir = scandir($strBackgroundDir);
						
			foreach ($aryDir as $strFile)
			{
				if (is_dir($strFile))
				{
					continue;
				}
				if ($strFile == "." || $strFile == "..")
				{
					continue;
				}
				if (!file_exists($strBackgroundDir . "/" . $strFile))
				{	
					continue;
				}
								
				fwrite($res, $strBackgroundDir . "/" . $strFile . "\n");
			}	
		}
		elseif (file_exists($strBackgroundDir))
		{
			fwrite($res, $strBackgroundDir);
		}
	}
	
	fclose($res);
}

/**
 * php4 compat for scandir
 * taken from php.net/scandir user comments
 */
if(!function_exists('scandir')) {
	function scandir($strDir, $intSortorder = 0) {
		if (is_dir($strDir)) {
			$strDirlist = opendir($strDir);
			while (($strFile = readdir($strDirlist)) !== false) {
				if(!is_dir($strFile)) {
					$aryFiles[] = $strFile;
				}
			}
		($intSortorder == 0) ? asort($aryFiles) : rsort($aryFiles);
		return $aryFiles;
		} else {
			return false;
		}
	}
}

// }}}

// {{{ main

rewriteBackgroundList();
exec("killall -USR1 xfdesktop");

// }}}
?>
[/php]

---

### Post by ruiferreira on 2007-01-15
Try gaze.sourceforge.net it's a nice wallpaper switcher that fetches images from flickr. Just works with gnome, though :|

---

### Post by BlackTopBum on 2007-02-23
Thank you, this is somewhat sweet.  I say "somewhat" because if I'm not logged in cron sends the following message (25 of them last night alone <g>):

Cron <cmo@codybeau> killall -USR1 xfdesktop
xfdesktop: no process killed

Know of a way around this and yet allow switching images?  i *REALLY* like the changing wallpaper.

---

### Post by hyper_ch on 2007-02-24
could the output maybe piped to /dev/null?

e.g.

```

0,5,10,15,20,25,30,35,40,45,50,55 * * * * killall -USR1 xfdesktop | /dev/null

```

I've never tried that above so I have no clue whether this works... just a suggestion that you may want to try.

---

### Post by BlackTopBum on 2007-02-24
> **hyper_ch said:**
> could the output maybe piped to /dev/null?

e.g.

```

0,5,10,15,20,25,30,35,40,45,50,55 * * * * killall -USR1 xfdesktop | /dev/null

```

I've never tried that above so I have no clue whether this works... just a suggestion that you may want to try.

Thanks for writing ! Yes, you're right that you might be wrong <g>. I've thought it over and this works:

# Reload Background Image
*/30 * * * * killall -USR1 xfdesktop > /dev/null 2>&1

---

### Post by ramasdf123 on 2007-04-08
how can i get this to work on gnome?

---

### Post by BlackTopBum on 2007-04-08
You can't. Use this instead: [http://ubuntuforums.org/showthread.php?t=18163](http://ubuntuforums.org/showthread.php?t=18163)

---

### Post by gringogrande on 2007-04-16
Nice. Problem is that my computer has a tendency of freezing up during the changes, and when I'm playing games or watching movies, I'd prefer it to not switch, so I whipped up a little script that temporarily lowers it scheduling priority.

```
#!/bin/bash
#change-background

#get the pid for xfdesktop
pid=`ps -e | grep xfdesktop | gawk '{print $1}'`

#a regular expression containing the names of the processes
#that will defer the switching
deferred='(mplayer|xgame)'

if [[ -z $pid ]] && [[ -n `ps -e | egrep $deferred` ]]; then

else
    renice 19 -p $pid
    kill -USR1 $pid
    renice 0 -p $pid
fi
```

---

### Post by daynah on 2007-04-16
> **gringogrande said:**
> Nice. Problem is that my computer has a tendency of freezing up during the changes, and when I'm playing games or watching movies, I'd prefer it to not switch, so I whipped up a little script that temporarily lowers it scheduling priority.

```
#!/bin/bash
#change-background

#get the pid for xfdesktop
pid=`ps -e | grep xfdesktop | gawk '{print $1}'`

#a regular expression containing the names of the processes
#that will defer the switching
deferred='(mplayer|xgame)'

if [[ -z $pid ]] && [[ -n `ps -e | egrep $deferred` ]]; then

else
    renice 19 -p $pid
    kill -USR1 $pid
    renice 0 -p $pid
fi
```

I'm not smart like you. Is it on line 9 that I could change it to something like...

```

deferred='(mplayer|xgame|vlc)'

```
?

---

### Post by gringogrande on 2007-04-16
> **daynah said:**
> I'm not smart like you. Is it on line 9 that I could change it to something like...

```

deferred='(mplayer|xgame|vlc)'

```
?
Yes, exactly. Any process that contains the three letter combination 'vlc' (like wxvlc, for instance) will then disable the script from changing the background.

---

### Post by Cheese Sandwich on 2007-05-04
> **ramasdf123 said:**
> how can i get this to work on gnome?

[http://ubuntuforums.org/showthread.php?t=415255](http://ubuntuforums.org/showthread.php?t=415255)

---

### Post by kspn on 2007-06-24
> **gringogrande said:**
> Nice. Problem is that my computer has a tendency of freezing up during the changes, and when I'm playing games or watching movies, I'd prefer it to not switch, so I whipped up a little script that temporarily lowers it scheduling priority.

```
#!/bin/bash
#change-background

#get the pid for xfdesktop
pid=`ps -e | grep xfdesktop | gawk '{print $1}'`

#a regular expression containing the names of the processes
#that will defer the switching
deferred='(mplayer|xgame)'

if [[ -z $pid ]] && [[ -n `ps -e | egrep $deferred` ]]; then

else
    renice 19 -p $pid
    kill -USR1 $pid
    renice 0 -p $pid
fi
```

I used this script and it is working perfectly, thanks.

It makes life so much easier when things just work! I added an icon so that if I don't feel like using that image then I can switch to a new one.

Thanks for the tip.

---

### Post by gtr225 on 2007-12-14
Thanks, this helped.

---

### Post by dakal on 2008-06-13
I ended up using this crontab line to avoid trying to send signals to other users' xfdesktop processes:

```
*/10 * * * * kill -USR1 $(ps awxu | grep -E '^_loginname_[ \t]+.+[0-9:]+ /usr/bin/xfdesktop' | awk '{print $2}') >/dev/null 2>&1
```

Replace the underlined "loginname" with your login name.

---

### Post by blithen on 2008-06-20
I know I'm resurrecting the dead here, but this is AMAZING. Thanks a lot, works perfectly.

---

### Post by wildemad on 2009-09-01
Interesante.

Gracias por el how-to

Un saludo.

---

### Post by Kangarooo on 2010-06-18
I would suggest easyr is this.
After putting wallpaper list and installing cron
just open crontab -e
paste there just */5 * * * * export DISPLAY=:0; /usr/bin/xfdesktop -reload
save and exit with ctrl+shift+X and then Y and Enter
and thats it.
it will make every minute that can be divided by 5 to reload xfdesktop so basicly every 5 minuts

---

### Post by LoloftheRings on 2011-05-05
> **Kangarooo said:**
> I would suggest easyr is this.
After putting wallpaper list and installing cron
just open crontab -e
paste there just */5 * * * * export DISPLAY=:0; /usr/bin/xfdesktop -reload
save and exit with ctrl+shift+X and then Y and Enter
and thats it.
it will make every minute that can be divided by 5 to reload xfdesktop so basicly every 5 minuts

Old thread, but people might still be using this
I agree, reloading prevents any flickering from occurring. Also, killing the process about 5/6 times doesnt make it startup again for me. This does work however.

---

### Post by DaveAtFraud on 2012-12-11
> **BlackTopBum said:**
> Thank you, this is somewhat sweet.  I say "somewhat" because if I'm not logged in cron sends the following message (25 of them last night alone <g>):

Cron <cmo@codybeau> killall -USR1 xfdesktop
xfdesktop: no process killed

Know of a way around this and yet allow switching images?  i *REALLY* like the changing wallpaper.

[dave@petard ~]$ crontab -l
*/5 * * * * /usr/bin/who | /bin/grep -E "dave *tty1" 2>&1 > /dev/null && /usr/bin/xfdesktop --display=:0 --reload 2>&1 > /dev/null

If I'm logged in, I get a tty.  The grep -E matches what comes back from the who command.  If the grep fails, I'm not logged in and the result is "false" so the && short circuits and fails without executing the right side of the &&.  If I'm logged in, the grep succeeds and the right side of the && has to be evaluated.

Cheers,
Dave

---

