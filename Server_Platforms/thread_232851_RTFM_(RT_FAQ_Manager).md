---
title: "RTFM (RT FAQ Manager)"
date: 2006-08-09
forum: Server Platforms
---

### Post by Viruk on 2006-08-09
I am having trouble with RT FAQ Manager. I managed to get a server set up and RT installed and apparently working. I am now moving on to RT FAQ Manager but I am having difficulty (I think mainly due to my lack of linux/ubuntu knowledge).

I have read the install instructions on the RT FAQ Manager website [http://www.bestpractical.com/rtfm/](http://www.bestpractical.com/rtfm/) (the instructions are in the acrobat file there - they are that brief I will paste them here though):

Installing RTFM
1. Install RT 3.0.x
2. Once RT 3.0 appears to be happily installed, cd into the directory you unpacked RTFM into.
3. Edit RTFM's makefile to point to your RT 3 instance.
4) Make sure that MySQL's or pgsql's commandline tool is in your path.
5. Type make install
6. Stop and start your web server

1. done, I have that working from the package that is available for this software (I used a how-to from [http://howtoforums.net/viewtopic.php?t=48](http://howtoforums.net/viewtopic.php?t=48) and got the packages I needed using apt-get install request-tracker3.4 rt3.4-apache2 rt3.4-clients apache2-doc postfix postgresql postgresql-doc-7.4 lynx
2. I managed to copy this via WinSCP, and extracted the tar file using the command line
3. this is where I get lost, I have had a read around but I am not sure how this file should be edited
The file looks like this:
use inc::Module::Install;
RTx('RT-FM');
name('RTFM');
version_from('lib/RT/FM.pm');
license('GPL version 2');
requires(perl  => 5.008);
requires('Text::WikiFormat');
requires(RT => '3.4.2',
    Tree::Simple => 0,
    HTML::TreeBuilder => 0,
    Time::ParseDate => 0,
    HTML::FormatText => 0,
    YAML => 0

);
&WriteAll;

4. I am also unsure what the command line tool is. I am using postgresql, but I am not sure what the program/tool is actually called or where it resides on an ubuntu server

5. I'm sure I could manage that if I got the command line tool in the right place (or extracted the tar in the right place if you look at it that way!)

6. I'm sure I could handle that 

Due to my problems with the above process I looked for (and found) a package for RTFM at [http://packages.ubuntu.com/dapper/misc/rtfm](http://packages.ubuntu.com/dapper/misc/rtfm)

I managed to install it using apt-get, but now I am stuck as I dont know what configuration is required and RT doesn't appear to have picked up RTFM automatically.

Has anyone out there used this package? 
Can anyone reccomend any resources or "how to"s?
Or can anyone help me with resolving points 3 or 4 in the installation instructions?

Any help with any of the above would be greatly appreciated.
Thank you in advance =)

---

