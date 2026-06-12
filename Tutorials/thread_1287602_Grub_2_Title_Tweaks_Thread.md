---
title: "Grub 2 Title Tweaks Thread"
date: 2009-10-10
forum: Tutorials
---

### Post by drs305 on 2009-10-10
[COLOR=MAROON][B][SIZE=4][CENTER]*Grub 2 (Title) Tweaks*[/CENTER]
[/SIZE][/B][/COLOR]
[SIZE=2][CENTER]or the[/CENTER]
[/SIZE]

[COLOR=MAROON][B][SIZE=3][CENTER]*UPDATE: The Day Has Arrived When This Guide Becomes Largely Unneccesary*[/CENTER]
[/SIZE][/B][/COLOR]
Daniel Richter has developed a great GUI app which can do simply and quickly what the following command-line actions accomplish. I highly recommend you visit my [_Grub Customizer_]("http://ubuntuforums.org/showthread.php?p=10340183#post10340183") thread and try his application.


[COLOR=MAROON][B][SIZE=3][CENTER]*I Don't Want It to Say "Microsoft Windows Vista Home Edition" Thread*[/CENTER]
[/SIZE][/B][/COLOR]


**[COLOR=Navy][SIZE=3]Purpose[/SIZE][/COLOR]**
This thread offers tweaks to the Grub 2 *10_linux* and *30_os-prober* files in /etc/grub.d. The purpose is to change the way ***Titles*** are displayed on the Grub 2 menu. 

With the exception of the "But First" section, the tweaks in this thread are outside the normal options currently available in Grub 2's /etc/default/grub. As Grub 2 options are incorporated by the developers these scripts will be annotated or removed. ***Before you get too deep into editing these scripts, remember you can also simply create a custom menu in which you can use your own titles, include or omit boot options, etc***. See *meierfra's* page for creating a [custom menu]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu").

If you are looking for an introduction on how Grub 2 works, please visit [Grub 2]("https://help.ubuntu.com/community/Grub2") (Ubuntu Community Help doc), [_Grub 2 Basics_]("http://ubuntuforums.org/showthread.php?t=1195275") or [_Grub 2 Introduction_]("http://ubuntuforums.org/showthread.php?t=1285897") elsewhere on the Ubuntu Forums. This thread also does not discuss custom configuration files such as /etc/grub.d/40_custom although these tweaks could be incorporated therein.

Feel free to post your tweaks but please limit this thread to posts concerning the Grub text you see in the menu.  Also suggest improvements to the ones I posted - I'll edit them to keep them udpated. See the end of this post for some suggestions.

Hopefully as the capabilities of Grub 2 are expanded or become better understood many of these tweaks will become unnecessary. In the meantime those truly anal among us who can never leave things alone will have a place of refuge.

**[COLOR=Navy][SIZE=3]Tweaks This Guide Covers[/SIZE][/COLOR]**
[LIST]
[*]Remove MEMTEST86+
[*]Remove Recovery Mode
[/LIST]
[LIST=1]
[*]Changing/Limiting Ubuntu & Linux Titles
[*]Limiting the Number of Main Linux Kernel Entries
[*]Changing Windows/Other OS Titles
[*]Hiding the Recovery/Single User Partition
[*]Hiding Memtest
[*]Hiding the Windows Recovery Partition
[*]Changing "Windows Recovery Environment (loader)"
[*]Hiding Other Partitions
[*]Hiding the 32/64 bit OSX Entry When Both Appear
[*]Changing Menu Entry Order
[*]Hiding the Menu on Multi-OS Computers
[*]Hiding Partitions Using Parttool
[*]Removing the Grub 1.99 Submenu
[*]Troubleshooting
[*]Custom Menus
[*]Custom Tweaks Provided by Others in This Thread
[*]Get the Splash Screen to Display before the Menu (See [Post #233]("http://ubuntuforums.org/showpost.php?p=12093605&postcount=233"))
[/LIST]


**[COLOR=Navy][SIZE=3]Background[/SIZE][/COLOR]**
Grub 2 displays, unlike Grub, are not controlled by a single file but rather by the settings in /etc/default/grub and a series of script files located in /etc/grub.d/ . These scripts determine, in part, how the menu options are transferred into /boot/grub/grub.cfg and the menu you see on boot.

See [_Grub 2 Basics_]("http://ubuntuforums.org/showthread.php?t=1195275") for a general overview of Grub 2 and for links to other Grub 2 resources.

[SIZE=3]**[COLOR=Navy]Before You Start[/COLOR]**[/SIZE]
[LIST=1]
[*]Make copies of the system files you will be altering.
Note: If you leave the .bak files executable and in the /etc/grub.d folder they will be run by update-grub.
```

sudo cp /etc/grub.d/10_linux /etc/grub.d/10_linux.bak
sudo cp /etc/grub.d/30_os-prober /etc/grub.d/30_os-prober.bak
sudo chmod -x /etc/grub.d/*.bak

```
[*]**Make sure you are working in the correct file, and in the applicable section of that file.**
[*]**Run "sudo update-grub" to incorporate the changes into Grub 2's menu.**
[*]When defining variables, the [SIZE=4]**`**[/SIZE] symbol is not a straight quote symbol but a 'grave'. It is often found near the top left of the keyboard.
[*]**[COLOR="DarkRed"]Wubi Users:[/COLOR]** Replace all instances of 10_linux to 10_lupin in */etc/grub.d/*
[/LIST]


**[COLOR=Navy][SIZE=3]Built-In Settings and Non-Tweak Ways to Limit Menu Entries[/SIZE][/COLOR]**
[LIST]
[*][SIZE=3][COLOR=DarkRed]**Removing Older Kernels**[/COLOR][/SIZE]
If you are just seeing too many versions of the Linux kernel (including the associated recovery option), you can reduce the number by physically removing them from your machine. While it's best to keep at least one older kernel as a backup, others can be removed. Perhaps the easiest method to remove extra kernels is to install *Ubuntu-Tweak* from [http://ubuntu-tweak.com/]("http://ubuntu-tweak.com/"). Details on how to use Ubuntu-Tweak to remove kernels can be found in  [this HOWTO]("http://ubuntuforums.org/showthread.php?t=1587462").  Alternatively, you can use Synaptic and search for "linux-image" and select the lower-numbered kernels you no longer use. An example would be "linux-image-2.6.31-9-generic". You could also remove the "linux-header...." for the same kernel number. Once they are removed, run "sudo udpate-grub" and your menu will be less cluttered.


[*][SIZE=3][COLOR=DarkRed]**Turn Off "MEMTEST86+"**[/COLOR][/SIZE]
There is no setting to turn off the "memtest86+" option in */etc/default/grub* but you can eliminate these entries by turning off the script that searches for them. The following command removes the "executable" bit from the */etc/grud.d/20_memtest86+* file. To restore the setting, change the "-" to a "+":
```

sudo chmod -x /etc/grub.d/20_memtest86+

```
[LIST]
[*]This effects only the system partition. If you have multiple partitions with Linux installations there is a tweak later that will turn off *memtest86+* on them as well.
[*]In the Tweaks section there is an explanation of how to boot into the "Recovery Mode" even without a menu option.
[/LIST]
 
[*][SIZE=3][COLOR=DarkRed]**Turn Off Recovery Mode**[/COLOR][/SIZE]
If you don't want to see the Recovery Mode Options for *any* item, change the setting in */etc/default/grub*.  While it may be a good idea to have the "Recovery" mode option displayed, if you don't want it, here is how to get rid of it. 


You can do this by opening the file as 'root' with any text editor and removing the # symbol from the beginning of the line,  or by running the following command. 
```

sudo sed s/'#GRUB_DISABLE_LINUX_RECOVERY="true"'/'GRUB_DISABLE_LINUX_RECOVERY="true"'/g -i /etc/default/grub

```
[/LIST]


[SIZE=3]**[COLOR=Navy]Grub 2 Files[/COLOR]**[/SIZE]
The basic configuration settings are made in /etc/default/grub. This thread will not deal with those settings.
The two primary files altered by tweaks in this thread are:
[LIST]
[*]/etc/grub.d/10_linux
[LIST]
[*]This file contains instructions and scripts which deal with linux kernels on the default system partition.
[/LIST]
 
[*]/etc/grub.d/30_os-prober
[LIST]
[*]This file contains instructions and scripts to deal with kernels and other operating systems found on other partitions.
[*]The file contains four sections. Changes must be made in the correct section, as changes in one section will not effect the scripts in the other sections.
[LIST]
[*]The four sections are for Windows, other Linux installations, OSX, and Hurd.
[/LIST]
 
[/LIST]
 
[/LIST]


[SIZE=3]**1. [SIZE=3][B][COLOR=DarkRed]CHANGING/LIMITING UBUNTU & LINUX TITLES[/COLOR]**[COLOR=Navy] (on default partition)[/COLOR][/SIZE] - [COLOR=Navy] /etc/grub.d/10_linux[/COLOR][/B][/SIZE] [SIZE=4]**[COLOR=DarkRed]*[/COLOR]**[/SIZE]

[LIST]
[*][SIZE=3]**A. Changing Linux Titles on Main Partition**[/SIZE]

```
gksu gedit /etc/grub.d/10_linux
```
[LIST]
[*]New: Starting with Grub 1.98, the user can change the codename (Ubuntu, Kubuntu, etc) from the */etc/default/grub* file. The entry to add is "GRUB_DISTRIBUTOR=", which will replace "Ubuntu" in the menuentry with whatever is entered in this setting. Example: GRUB_DISTRIBUTOR=MyLinux will produce an entry of "MyLinux, with Linux 2.6.35-23-generic" 

[*]Defined Variable Examples:  **${OS}** *Ubuntu, Kubuntu*, etc.; **${version}** *2.6.32-25, 2.6.32-25-generic*, etc.
Added Variable Example:  **${codename}** *lucid*
[*]Add new variables ***[COLOR=Navy]codename[/COLOR]*** and ***[COLOR=Navy]version_no_generic[/COLOR]***. The list of variables in 10_linux begins at approximately line 118.
[LIST]
[*]If *Recovery* modes are displayed, make the change in that section as well. It's the next section of 10_linux.
[/LIST]
[LIST]
[*]```

while [ "x$list" != "x" ] ; do
  linux=`version_find_latest $list`
  echo "Found linux image: $linux" >&2
  basename=`basename $linux`
  dirname=`dirname $linux`
  rel_dirname=`make_system_path_relative_to_its_root $dirname`
  version=`echo $basename | sed -e "s,^[^0-9]*-,,g"`
  alt_version=`echo $version | sed -e "s,\.old$,,g"`
  linux_root_device_thisversion="${LINUX_ROOT_DEVICE}"
# User-added variable
  [B][COLOR=Navy]codename="`lsb_release -cs`"
  version_no_generic="`echo ${version} | cut -d "-" -f 1-2`"[/COLOR][/B]

```

[SIZE=3]**Original: [COLOR=DarkRed]Ubuntu*, Linux* 2.6.32-25[/COLOR]**[/SIZE]
This should be located at approximately line 144.
**[SIZE=3]New: [COLOR=DarkGreen]Ubuntu 2.6.32-25[/COLOR][/SIZE]**
Change the original line above to look like the following by removing "**[COLOR=Red], Linux[/COLOR]**": 
```

[COLOR="DarkRed"]# Old code[/COLOR]   # New code
[COLOR="DarkRed"]#  if ${recovery} ; then
#    title="$(gettext_quoted "%s, with Linux %s (recovery mode)")"
#  else
#    title="$(gettext_quoted "%s, with Linux %s")"
#  fi
[/COLOR]
  if ${recovery} ; then
    title="$(gettext_quoted "%s %s (recovery mode)")"
  else
    title="$(gettext_quoted "%s %s")"
  fi

```

[SIZE=3]**New: [COLOR=DarkGreen]lucid 2.6.32-25[/COLOR]**[/SIZE]
Ensure the variable **${codename}** has been added into the file's variable list.
The codename returned in this script will always be the current codename of your present Linux OS (i.e. karmic, lucid, etc.).
Change the original line at approximately 148 to look like the following (also change the same line in the Recovery section several lines down):
```

[COLOR="DarkRed"]#linux_entry "${OS} ${version}" \[/COLOR]
linux_entry "[COLOR="Navy"]${codename}[/COLOR] ${version}" \

```


[/LIST]
[SIZE=2]
[*]Run "sudo update-grub" to update the Grub 2 Menu.[/SIZE]
[*]Note: If you want to capitalize the codename (Hardy, Lucid, Maverick) see [post #38]("http://ubuntuforums.org/showthread.php?t=1287602#38").
[/LIST]
[SIZE=4]**[COLOR=DarkRed]*[/COLOR]**[/SIZE] Wubi users should make the changes to */etc/grub.d/10_lupin* rather than */etc/grub.d/10_linux*
[/LIST]

[SIZE=3]**2. [COLOR=DarkRed]LIMITING MAIN KERNEL ENTRIES[/COLOR]**[/SIZE] 
New for Grub 1.99: Older kernels will be placed in a submenu and will not be visible on the main Grub2 menu. The older kernels can be accessed by selecting the submenu entry. This guide currently does not cover hiding kernels displayed in the submenu.

**Grub 1.98 & Earlier: **When a new kernel is introduced, it is automatically entered into the Grub 2 menu. Over time, the number of kernels listed may become quite long. The number of the current system kernels displayed can be changed via script editing (the kernels remain on the system but not displayed) or physically removing the kernels from the system via APT (command line, Synaptic, etc). 

With this tweak, you will be able to set the number of main OS Linux kernels (plus their associated Recovery modes if enabled) you want to see on the menu. The variable will be called LINUX_KERNELS_DISPLAYED. In this example, two kernels will be listed on the menu. Edits will be made to */etc/grub.d/10_linux* and will affect only the primary partition's Linux kernels.

Note this tweak does not remove kernels from your system or free up disk space. See the section on removing older kernels in the "Before You Start" section if you want to physically remove the kernels from the system.

Find this section of */etc/grub.d/10_linux* in Grub 1.98 (approximately line 116). **Note this is not the entire file!**. Added sections are in **[COLOR="DarkRed"]bold dark red[/COLOR]**:
> 
prepare_boot_cache=

[B][COLOR="DarkRed"]# Added to limit number of Linux kernels displayed.
COUNTER=0
LINUX_KERNELS_DISPLAYED=[COLOR="Blue"]2[/COLOR]
#[/COLOR][/B]

while [ "x$list" != "x" ] ; do
  linux=`version_find_latest $list`
  echo "Found linux image: $linux" >&2
.....
.....  < omitted lines >
.....  < several lines from the bottom of the file >

  list=`echo $list | tr ' ' '\n' | grep -vx $linux | tr '\n' ' '`

[B][COLOR="DarkRed"]
# Added to limit number of Linux kernels displayed.
COUNTER=`expr $COUNTER + 1` 
if [  $COUNTER -eq $LINUX_KERNELS_DISPLAYED ]; then
  list=""
fi
#
[/COLOR][/B]
  done

Save the file and update-grub.

[SIZE=3]**3. [COLOR=DarkRed][SIZE=3][B]CHANGING WINDOWS/OTHER OS TITLES** (including Linux)[/SIZE][/COLOR] - [COLOR=Navy] /etc/grub.d/30_os-prober[/COLOR][/B][/SIZE] 
This file is divided into sections for various types of operating systems. The first section is for Windows (OS), the second Linux (linux), the third OSX (macosx), and finally Hurd (hurd).

```
gksu gedit /etc/grub.d/30_os-prober
```[SIZE=3]A. **Changing [COLOR=DarkGreen]Windows[/COLOR] Entries**[/SIZE]
[LIST]
[*]Changes made via this method are best done to OS or kernels which the user does not expect to change. If the system detects a title change the entry in #3 may no longer be correct.

[SIZE=3]**Placing Windows at the Top of the Menu: **[/SIZE] 
Although you can make Windows the default by with the 'GRUB_DEFAULT' setting in /etc/default/grub, if you really want Windows to be the first item on the menu there are two fairly easy ways to do it.
[LIST]
[*]Rename */etc/grub.d/30_os-prober*
If you only have one Ubuntu partition and Windows, renaming */etc/grub.d/30_os-prober* to */etc/grub.d/09_os-prober* will place Windows at the top of the list

[*]Create a */etc/grub.d/06_custom* menu.
Creating a custom file in the /etc/grub.d folder with a beginning number of 06 will place it's contents before any of the standard menu entries. To create the *06_custom* file, open */etc/grub.d/40_custom* for editing as root. Below the existing lines, copy the complete Windows menu entry from */boot/grub/grub.cfg*. 

The entry will start with the "menuentry" line and end with "}" on a single line by itself. Make the file executable ( sudo chmod +x /etc/grub.d/06_custom ) and update-grub.
[/LIST]

[SIZE=3]**Original: [COLOR=DarkRed]Microsoft Windows XP Home Edition (on /dev/sda1)[/COLOR]**[/SIZE] 

1. Run this command to get the current Grub 2 menu entries:
```

sudo cat /boot/grub/grub.cfg | grep "menuentry" | cut -d '"' -f 2

```

[SIZE=3]**New: [COLOR=DarkGreen]Whatever (on /dev/sda7)[/COLOR]**[/SIZE]
2. This section appears around line 150 of the file. Replace the section in [COLOR=Red]red[/COLOR]. 
3. Copy the exact title you wish to change (Example: *Microsoft Windows XP Home Edition* ) and place it between the quotes in the first line below. Note the title **[COLOR="DarkRed"]does not include the portion [COLOR="Blue"]"(on /dev/sdXX)"[/COLOR][/COLOR]**
Enter the *desired title* between the quotes in the second line below - in this example, "Windows XP" would replace "Enter Desired New Title Here".
```

[COLOR="DarkRed"]# Old code[/COLOR]   # New code  [COLOR="Red"]# Old Title[/COLOR]  [COLOR="DarkBlue"]# New Title[/COLOR]
[COLOR="DarkRed"]# if [ -z "${LONGNAME}" ] ; then
#    LONGNAME="${LABEL}"
# fi[/COLOR]

  if [ "${LONGNAME}" = "**[COLOR=Red]Enter Exact Title You Just Copied[/COLOR]**" ] ; then
    LONGNAME="**[COLOR=DarkBlue]Enter Desired New Title Here[/COLOR]**"
  elif [ -z "${LONGNAME}" ] ; then
    LONGNAME="${LABEL}"
  fi

```

5. Multiple entries can be made in the same section:
```

  if [ "${LONGNAME}" = "**[COLOR=Red]Enter Exact Title You Just Copied[/COLOR]**" ] ; then
    LONGNAME="**[COLOR=DarkBlue]Enter Desired New Title Here[/COLOR]**"
  elif [ "${LONGNAME}" = "**[COLOR=Red]Enter Second Title You  Copied[/COLOR]**" ] ; then
    LONGNAME="**[COLOR=DarkBlue]Enter Desired Second Title Here[/COLOR]**"
  elif [ -z "${LONGNAME}" ] ; then
    LONGNAME="${LABEL}"
  fi

```
[/LIST]

[SIZE=3]B. **Changing Other [COLOR=DarkGreen]Linux[/COLOR] Installations**[/SIZE]
[LIST=1]
[*]Included in the first codeblock below are all the **[COLOR=Navy]user-defined[/COLOR]** variables used in this section of the guide. They apply to the "linux" section of /etc/grub.d/30_os-prober file. 
It is only necessary to insert the ones you wish to use. For simplicity and space-saving, they have all been included in the first codeblock below.
[*]Defined Variables Examples:  **${LONGNAME}** Microsoft Windows XP Home Edition, Ubuntu 10.04 (9.04); **${DEVICE}** *sda1, sdb6*, etc; **${LLABEL}** Ubuntu, linux 2.6.32-25
[*] Find the linux section of the file at approximately line 170 (before other additions).
[*] Add the variables you wish to use from the examples below. Following the added variables are examples of possible returned value:
**${newtitle}**  Ubuntu 10.04  ;**${shortkernel}**  2.6.32-25 ; **${nomemtest}**  memtest86+ ; **${nosingle}**  single ; **shortdevice** (sda5) ; **${hidekernel}** 2.6.32
```

    ;;
    linux)
      LINUXPROBED="`linux-boot-prober ${DEVICE} 2> /dev/null | tr ' ' '^' | paste -s -d ' '`"

      for LINUX in ${LINUXPROBED} ; do
        LROOT="`echo ${LINUX} | cut -d ':' -f 1`"
        LBOOT="`echo ${LINUX} | cut -d ':' -f 2`"
        LLABEL="`echo ${LINUX} | cut -d ':' -f 3 | tr '^' ' '`"
        LKERNEL="`echo ${LINUX} | cut -d ':' -f 4`"
        LINITRD="`echo ${LINUX} | cut -d ':' -f 5`"
        LPARAMS="`echo ${LINUX} | cut -d ':' -f 6- | tr '^' ' '`"
# User-added variables
    [B][COLOR=DarkBlue]newtitle=`echo ${LONGNAME} | cut -d " " -f 1-2`
    shortkernel="`echo ${LKERNEL} | cut -d "-" -f 2-4`"
        shortdevice="`echo ${DEVICE} | cut -d "/" -f 3`"           
        nomemtest="`echo ${LLABEL} | cut -d " " -f 1`"
        nosingle="`echo ${LPARAMS} | sed 's/^.* //'`"
        hidekernel-all="`echo ${LKERNEL} | cut -d'-' -f2`"
        hidekernel-one="`echo ${LKERNEL} | cut -d'-' -f2-3`"
[/COLOR][/B]

```

[SIZE=3]**Original: [COLOR=DarkRed]*Linux,* Ubuntu 10.04  2.6.32-25 (on /dev/sda7)[/COLOR]**[/SIZE] 
Modify the entry in [COLOR=Red]red[/COLOR] for each section you want to change (approximately line 193 in original file):
[SIZE=3]**New Format: [COLOR=DarkGreen]Ubuntu 10.04  2.6.32-25 (on /dev/sda7)[/COLOR]**[/SIZE]
```

[COLOR="DarkRed"]# Old code[/COLOR]   # New code  
[COLOR="DarkRed"]#        cat << EOF
#menuentry "${LLABEL} (on ${DEVICE})" {
#EOF[/COLOR]
        cat << EOF
menuentry "${newtitle}  ${shortkernel}  (on ${DEVICE})" {
EOF

```

[SIZE=3]**New: [COLOR=DarkGreen]Ubuntu 10.04  2.6.32-25[/COLOR]**[/SIZE]
```

[COLOR="DarkRed"]# Old code[/COLOR]   # New code  **[COLOR="DarkBlue"]# New Variable[/COLOR]**
[COLOR="DarkRed"]#        cat << EOF
#menuentry "${LLABEL} (on ${DEVICE})" {
#EOF[/COLOR]
        cat << EOF
menuentry "**[COLOR="DarkBlue"]${newtitle}  ${shortkernel}[/COLOR]**" {
EOF

```
[/LIST]

[SIZE=3]**C. Eliminating or Changing "[COLOR=DarkRed]*(on /dev/sdX)*[/COLOR]"**[/SIZE]
[LIST]
[*]There are specific sections for Windows (OS), Linux (linux), and OSX (macosx). Users must find the section(s) they wish to change or do a universal search/replace.
[*]Defined Variables:  **${LONGNAME}** OS title; **${device}** Partition location (e.g. sda1, sdb6, etc)
[*]Modify the entry in [COLOR=Red]red[/COLOR] for each section you want to change.

[SIZE=3]**Original: [COLOR=DarkRed]Windows XP Home *(on /dev/sda7)*[/COLOR]**[/SIZE] 
Approximately line 144.
```

[COLOR="Red"]menuentry "${LONGNAME} (on ${DEVICE})" {[/COLOR]

```

[SIZE=3]**New: [COLOR=DarkRed]Windows XP Home [/COLOR] [COLOR=DarkGreen](sda1)[/COLOR]**[/SIZE] 
```

menuentry "${LONGNAME}**[COLOR=Navy] (${shortdevice})" {[/COLOR]**

```
[SIZE=3]**New: [COLOR=DarkRed]Windows XP Home [/COLOR]**[/SIZE] 
```

menuentry "${LONGNAME}" {

```
[SIZE=3]**Original: [COLOR=DarkRed]Linux, Ubuntu 10.04  2.6.32-25 *(on /dev/sda7)*[/COLOR]**[/SIZE] 
Approximately line 193.
```

[COLOR="Red"]menuentry "${LLABEL} (on ${DEVICE})" {[/COLOR]

```
[SIZE=3]**New: [COLOR=DarkRed]Linux, Ubuntu 10.04  2.6.32-25[/COLOR] [COLOR=DarkGreen](sda7)[/COLOR]**[/SIZE] 
```

menuentry "${LLABEL}**[COLOR=Navy] (${shortdevice})" {[/COLOR]**

```
[SIZE=3]**New: [COLOR=DarkRed]Linux, Ubuntu 10.04  2.6.32-25[/COLOR]**[/SIZE] 
```

menuentry "${LLABEL}" {

```
[/LIST]


[SIZE=3]**D. Hiding a [COLOR=DarkRed]Specific Kernel[/COLOR]** (All Examples use 2.6.26...  Substitute the kernel you desire to replace) [/SIZE]
[LIST]
[*]There are two components necessary for this option:
[LIST]
[*]The Variable, entered into either /etc/grub.d/10_os-prober, or the linux section of /etc/grub.d/30_os-prober. For the location of the variables, see Section 1 for main kernel variables or Section 2B for linux variables on other partitions.
[*]The Conditional Statement: **[COLOR=Navy]if [ ${hidekernel} = "X.X.XX" or "X.X.XX-X" or "X.X.XX-X-generic" ]; then[/COLOR]** # Use the appropriate kernel format.
[/LIST]

[LIST]
[*]X.X.XX or X.X.XX-XX example: 2.6.28 or 2.6.28-12
[/LIST]
 
[*]The [COLOR=DarkGreen]dark green items[/COLOR] are lines to be inserted into the script. The [COLOR=Red]red items[/COLOR] are those which must be tailored by the user. The [COLOR=Navy]dark blue items[/COLOR] are variables to be inserted in the appropriate area of the script.
[/LIST]
 

[LIST]
[*]**[SIZE=3]To Hide a Kernel on the main partition [/SIZE][SIZE=2] & listed in the *10_linux section* of /boot/grub/grub.cfg:[/SIZE]**
[LIST]
[*]The Variable is pre-defined - no additional user entry is required: [COLOR=Navy]${version}[/COLOR]"
[*]The Conditional Statement: **[COLOR=Navy]if [ ${version} != "X.X.XX" ]; then[/COLOR]**
[LIST]
[*]X.X.XX or X.X.XX-XX or X.X.XX-X-generic : 2.6.28 or 2.6.28-12 or 2.6.28-12-generic
[*]Note the "!=" translates to "Run this unless the entry is equal to the following".
[/LIST]
 
[/LIST]
1. Determine the kernel you want to hide (Example: 2.6.26 ) and change the code below in /etc/grub.d/10_linux at approximately line [noparse]144[/noparse]. 
```

[COLOR=DarkGreen]if [ ${version} != "[/COLOR][COLOR=Red]2.6.32-25-generic[/COLOR][COLOR=DarkOliveGreen]" ]; then[/COLOR]
  linux_entry "${OS}, Linux ${version}" \
      "${GRUB_CMDLINE_LINUX} ${GRUB_CMDLINE_EXTRA} ${GRUB_CMDLINE_LINUX_DEFAULT}" \
      quiet
  if [ "x${GRUB_DISABLE_LINUX_RECOVERY}" != "xtrue" ]; then
    linux_entry "${OS}, Linux ${version} (recovery mode)" \
    "single ${GRUB_CMDLINE_LINUX}"
  fi
[COLOR=DarkGreen]fi[/COLOR]

```
[/LIST]
 

[LIST]
[*]**[SIZE=3]To Hide All Instances of a Kernel on Another Partition[/SIZE][SIZE=2]:[/SIZE]**
[LIST]
[*][COLOR=Navy]hidekernel-all="`echo ${LKERNEL} | cut -d'-'[/COLOR] **[COLOR=DarkRed]-f2[/COLOR]**`"
[*]if [ ${hidekernel-all} = "[COLOR=DarkRed]2.6.26[/COLOR]" ]; then
[/LIST]


[*]**[SIZE=3]To Hide a Specific Kernel on Another Partition [/SIZE][SIZE=2]( in the *30_os-prober* section of /boot/grub/grub.cfg :[/SIZE]**
[LIST]
[*][COLOR=Navy]hidekernel-one="`echo ${LKERNEL} | cut -d'-'[/COLOR] **[COLOR=DarkRed]-f2-3[/COLOR]**`"
[*]if [ ${hidekernel-one} = "[COLOR=DarkRed]2.6.26-11[/COLOR]" ]; then
[/LIST]

1. Add the variable(s) to the linux variable list (approximately line 175).
```

        [B][COLOR=DarkSlateBlue]
        hidekernel-all="`echo ${LKERNEL} | cut -d'-' -f2`"
        hidekernel-one="`echo ${LKERNEL} | cut -d'-' -f2-3`"[/COLOR][/B]

```
2. Determine the kernel(s) you want to hide (Example: 2.6.26 ) and include it in linux section of /etc/grub.d/30_os-prober, at approximately line 183).
```

        if [ -z "${LLABEL}" ] ; then
          LLABEL="${LONGNAME}"
        fi

        [B][COLOR=DarkGreen]
        if [ ${hidekernel-**XXX**} = "[COLOR=Red]2.6.26[/COLOR]" ]; then   # Change **XXX** to 'one' or 'all'
       continue
    fi[/COLOR][/B]

        cat << EOF
menuentry "${LLABEL} (on ${DEVICE}" \
EOF

```

[SIZE=3]*[/SIZE] Note: os-prober can be disabled in various ways to prevent Grub 2 from searching any secondary partitions for bootable operating systems. See [_Grub 2 Basics_]("http://ubuntuforums.org/showthread.php?t=1195275") for more information.
[/LIST]


[SIZE=3]**4. [COLOR=DarkRed]Hiding Recovery/Single User Entries[/COLOR]** (from other partitions)[/SIZE]
[LIST]
[*]Grub 2 provides the ability to hide Recovery mode (single user) entries for the default partition without modifying the 10_linux or 30_os-prober files (see later in this section) .
[*]**Refer to the previous section for information on inserting variables.** The variable associated with hiding the Recovery mode (single-user) is [COLOR=DarkBlue]${nosingle}[/COLOR]. Make sure you add it to the variable list.
[*]The conditional statement below tells Grub to skip an entry if it is a recovery mode[/I] option. While a bit inelegant, when inserted in 30_os-prober it will effectively prevent the applicable options from appearing in the Grub 2 menu.
[*]To remove Recovery mode/single user entries *for other partitions found by 30_os-prober*:
[LIST]
[*]Insert the [COLOR=DarkGreen]code in green[/COLOR] just after the linux variable definitions and  before the first "menuentry" in the linux section (approximately line 180 before any additions).
```

        LINITRD="`echo ${LINUX} | cut -d ':' -f 5`"
        LPARAMS="`echo ${LINUX} | cut -d ':' -f 6- | tr '^' ' '`"
# User-added variables
    newtitle=`echo ${LONGNAME} | cut -d " " -f 1-2`
    shortkernel="`echo ${LKERNEL} | cut -d "-" -f 2-4`"
        shortdevice="`echo ${DEVICE} | cut -d "/" -f 3`"           
        [COLOR=Navy][B]
        nosingle="`echo ${LPARAMS} | sed 's/^.* //'`"
        hidekernel="`echo ${LKERNEL} | cut -d'-' -f2`"[/B][/COLOR]


        if [ -z "${LLABEL}" ] ; then
          LLABEL="${LONGNAME}"
        fi

        [B][COLOR=DarkGreen]
        if [ "${nosingle}" = "single" ]; then
       continue 
    fi[/COLOR][/B]

        cat << EOF
menuentry "${LLABEL} (on ${DEVICE}" \
EOF

```
[/LIST]
 
[*]To inhibit the display of recovery options on the *system partition*, uncomment or add this line to /etc/default/grub:
> 
GRUB_DISABLE_LINUX_RECOVERY=true

[*]Run "sudo update-grub" to incorporate these changes into the Grub menu.
[/LIST]


[SIZE=3]**5. [COLOR=DarkRed]Hiding MEMTEST+86[/COLOR]**[/SIZE]
[LIST]
The memtest86+ entry can be removed from the Grub2 menu by two methods.
[*]Change the file attribute.
[LIST]
[*]The memtest86+ entry can be removed from the menu simply by removing the executable bit from the /etc/grub.d/20_memtest86+ file.
[*]To make *memtest86+* non-executable, run the following commands:
```
sudo chmod -x /etc/grub.d/20_memtest86+ && sudo update-grub
```
[*]Note: *kansasnoob* has discovered that the memtest86+ entries generated from partitions containing a Grub legacy *menu.lst* file can be disabled by opening *the associated /boot/grub/menu.lst* file, finding the memtest86+ entry, and changing it to read: 
> # memtest86=false 
[/LIST]
[*]Change the scripts.

Insert the [COLOR=DarkGreen]code in green[/COLOR].

[LIST]
[*]In /etc/default/grub, add the following lines:
> 
GRUB_NOMEMTEST=true
export GRUB_NOMEMTEST

[*]In /etc/grub.d/20_memtest86+, add two lines in **[COLOR="DarkGreen"]dark green[/COLOR]**. (The second line is the last *fi* at the bottom of the quoted text):
> 
if test -e /boot/memtest86+.bin ; then
[B][COLOR="DarkGreen"]
if [ ! "x${GRUB_NOMEMTEST}" = "xtrue" ] ; then[/COLOR][/B]
  MEMTESTPATH=$( make_system_path_relative_to_its_root "/boot/memtest86+.bin" )
  echo "Found memtest86+ image: $MEMTESTPATH" >&2

  cat << EOF
menuentry "Memory test (memtest86+)" {
EOF
  printf '%s\n' "${prepare_boot_cache}"
  cat << EOF
	$LX	$MEMTESTPATH
}
menuentry "Memory test (memtest86+, serial console 115200)" {
EOF
  printf '%s\n' "${prepare_boot_cache}"
  cat << EOF
	$LX	$MEMTESTPATH console=ttyS0,115200n8
}
EOF
fi
**[COLOR="DarkGreen"]fi[/COLOR]**

[/LIST]
[*]Run "sudo update-grub" to incorporate these changes into the Grub menu.
[/LIST]


[SIZE=3]**6. [COLOR=DarkRed]HIDING THE  WINDOWS RECOVERY PARTITION (Vista)[/COLOR]**[/SIZE]

[LIST]
[*]GRUB 2 will find and create a menuentry for the Windows (Vista) Recovery partition. At least in Vista, the menu name is the same as the normal Vista operating partition, the only difference being the parttion designation. To remove the Recovery partition entry from the menu:
[LIST]
[*]Backup the existing /etc/grub.d/30_os-prober file, remove the executable bit from the backup so it isn't run during updates, and open the original for editing (the section starts around line 134):
[LIST]
[*]```
sudo cp /etc/grub.d/30_os-prober /etc/grub.d/30_os-prober.original  && sudo chmod -x /etc/grub.d/30_os-prober.original
gksu gedit +83 /etc/grub.d/30_os-prober &

```
[*]Determine the exact title and the Windows recovery partition. These can be located in the */boot/grub/grub.cfg* file. Add the highlighted entry below. In the example, the menuentry appeared as "Windows Vista (loader) (on /dev/sda1)". *Make sure you select the correct partition as the title may be the same for the normal and recovery titles.* The area in [COLOR=Red]bright red[/COLOR] should be the exact contents between the quotes in the menuentry for the recovery partition:
[*]> for OS in ${OSPROBED} ; do
DEVICE="`echo ${OS} | cut -d ':' -f 1`"
LONGNAME="`echo ${OS} | cut -d ':' -f 2 | tr '^' ' '`"
LABEL="`echo ${OS} | cut -d ':' -f 3 | tr '^' ' '`"
BOOT="`echo ${OS} | cut -d ':' -f 4`"

if [ -z "${LONGNAME}" ] ; then
LONGNAME="${LABEL}"
fi

[B][COLOR=DarkRed]# Added to remove Windows Recovery
if [ "$LONGNAME" = "[COLOR=Red]Windows Vista (loader)[/COLOR]" ] && [ "${DEVICE}" = "/dev/[COLOR=Red]sda1[/COLOR]" ] ; then
continue
fi
# End Added[/COLOR][/B]

[*]Save the file, then run:
```
sudo update-grub
```
[/LIST]
[/LIST]
[/LIST]

 
[SIZE=3][B]7. [COLOR=DarkRed]CHANGING "Windows Recovery Environment (loader)" to "Windows Vista" 
or Any Other Windows Title in the 30_os-prober Section of grub.cfg[/COLOR][/B][/SIZE]

[LIST]
[*]If Grub 2 mistakenly identifies the real Windows Vista partition as the Recovery Partition, use this section to rename the menu entry. In the example the new title is *Windows Vista*. You can change the "Windows Vista" title within the quotation marks to anything you wish:
[LIST]
[*]Backup the existing /etc/grub.d/30_os-prober file, remove the executable bit from the backup so it isn't run during updates, and open the original for editing (the section starts around line 134):
[LIST]
[*]```
sudo cp /etc/grub.d/30_os-prober /etc/grub.d/30_os-prober.original  && sudo chmod -x /etc/grub.d/30_os-prober.original
gksu gedit +83 /etc/grub.d/30_os-prober &

```
[*]Determine the exact title and the Windows recovery partition. These can be located in the */boot/grub/grub.cfg* file. Add the highlighted entry below. In the example, the menuentry appeared as "Windows Vista (loader) (on /dev/sda1)". *Make sure you select the correct partition as the title may be the same for the normal and recovery titles.* The area in [COLOR=Red]bright red[/COLOR] should be the exact contents between the quotes in the menuentry for the recovery partition:
[*]> for OS in ${OSPROBED} ; do
DEVICE="`echo ${OS} | cut -d ':' -f 1`"
LONGNAME="`echo ${OS} | cut -d ':' -f 2 | tr '^' ' '`"
LABEL="`echo ${OS} | cut -d ':' -f 3 | tr '^' ' '`"
BOOT="`echo ${OS} | cut -d ':' -f 4`"

if [ -z "${LONGNAME}" ] ; then
LONGNAME="${LABEL}"
fi

[B][COLOR=DarkRed]# Added to change "Windows Recovery Environment (loader)" to "Windows Vista"
if [ "$LONGNAME" = "[COLOR=Red]Windows Recovery Environment (loader)[/COLOR]" ] && [ "${DEVICE}" = "/dev/[COLOR=Red]sda1[/COLOR]" ] ; then
LONGNAME="[COLOR="Red"]Windows Vista[/COLOR]"
fi
# End Added[/COLOR][/B]

[*]Save the file, then run:
```
sudo update-grub
```
[/LIST]
[/LIST]
[/LIST]

 
[SIZE=3]**8. [COLOR=DarkRed]HIDING OTHER PARTITIONS[/COLOR]**[/SIZE]
You can hide any partition other than the system partition by editing */etc/grub.d/30_os-prober*. 

[LIST]
[*]To hide a partition with linux kernels, insert the **[COLOR="DarkGreen"]additional lines[/COLOR]**, substituting the correct drive/partition designations (sda3, sdb5, etc):
[LIST][*]        if [ -z "${LLABEL}" ] ; then
          LLABEL="${LONGNAME}"
        fi
       [COLOR="DarkGreen"][B]if [ "${LROOT}" = "/dev/sd[color="Red"]XY"[/color] ]; then
         continue
        fi[/B][/COLOR]
[/LIST]
[/LIST]


[LIST]
[*]To hide a Windows partition, insert the **[COLOR="DarkGreen"]additional lines[/COLOR]**,  substituting the correct drive/partition designations (sda3, sdb5,  etc):
[LIST][*]        if [ -z "${LONGNAME}" ] ; then
          LONGNAME="${LABEL}"
        fi
       [COLOR="DarkGreen"][B]if [ "${DEVICE}" =  "/dev/sd[color="Red"]XY"[/color] ]; then
         continue
        fi[/B][/COLOR]
[/LIST]
[/LIST]


[SIZE=3]**9. [COLOR=DarkRed]HIDING THE 32/64 BIT OSX ENTRY WHEN BOTH APPEAR[/COLOR]**[/SIZE]
If Grub 2 lists both 32-bit and 64-bit OSX entries and the user wishes to display only one or the other, edit */etc/grub.d/30_os-prober*:
Remove **either** of the following lines [noparse](approximately line 218)[/noparse] to remove the associated entry from the Grub 2 menu.
> 
      osx_entry xnu_kernel 32
      osx_entry xnu_kernel64 64

Run "sudo update-grub" after saving the file to incorporate the changes into the Grub 2 configuration file.


[SIZE=3]**10. [COLOR=DarkRed]CHANGING MENU ENTRY ORDER[/COLOR]**[/SIZE]
Two simple ways to change the basic order of entries appearing in the Grub 2 menu:
[LIST]
[*]Create a custom menu. */etc/grub.d/40_custom* menus will appear at the bottom of the menu. Rename the file 06_custom and the menu entries will appear at the top of the menu.
[*]Rename one (or more) of the existing */etc/grub.d* scripts. The scripts are run in order. So if you want the "Other OS" entries found by 30_os-prober to be run first (and placed first in the menu), simply rename 30_os-prober to 06_os-prober, 07_os-prober, etc or rename 10_linux to 99_linux, etc.
[/LIST]


[SIZE=3]**11. [COLOR=DarkRed]HIDING THE MENU ON MULTI-OS SYSTEMS[/COLOR]**[/SIZE]
By design, Grub 2 allows hiding the menu only on single-OS systems. This is established in the */etc/grub.d/30_os-prober* file. For users with multiple OS's on their machines, hiding the menu can be accomplished by altering the scripts. There are two ways to accomplish the task. The first edits only one file and eliminates a conditional; the second edits two files and adds a conditional, but is a bit more 'elegant'.

Shown are the applicable sections. Changes are highlighted in [COLOR="Red"]**bold red**[/COLOR]. The lines between the altered lines have been omitted.
[LIST]
[*]**Method 1.** Remove a conditional from */etc/grub.d/30_os-prober*.
For both Grub 1.97~beta (Karmic) and 1.98 (Lucid & later), the first line to edit is the same. It appears at approximately line 25-30 of */etc/grub.d/30_os-prober* in both versions.
> 
[COLOR="Red"]**# **[/COLOR] if [ "x${found_other_os}" = "x" ] ; then

The second change is to place a **[COLOR="DarkRed"]#[/COLOR]** symbol at the end of the conditional. There are many *if* statements, and it's important to find the correct nested *fi*. 

In Karmic, the nested *fi* comes just before the "GRUB_DISABLE_PROBER" section. If Lucid and later, it preceeds the "() adjust timeout" section.
Karmic (Grub 1.97~beta):
> 
      fi
    fi
[COLOR="Red"]**#  fi**[/COLOR]
}

if [ "x${GRUB_DISABLE_OS_PROBER}" = "xtrue" ]; then

Lucid & later (Grub 1.98+):
> 
**[COLOR="DarkRed"]#[/COLOR]**
  fi
}

adjust_timeout () {



[*]**Method 2.** Add a conditional.
This procedure modifies both */etc/grub.d/30_os-prober* and */etc/default/grub*. Open both with:
```
gksu gedit /etc/default/grub /etc/grub.d/30_os-prober
```
Add this line to */etc/default/grub*:
> 
[B][COLOR="DarkRed"]GRUB_FORCE_HIDDEN_MENU="true"
export GRUB_FORCE_HIDDEN_MENU[/COLOR][/B]

Change this line in */etc/grub.d/30_os-prober*, approximately line 25-30, 
From this:
> 
if [ "x${GRUB_DISABLE_OS_PROBER}" = "xtrue" ]; then

To this:
> 
  if [ "x${found_other_os}" = "x" ] || [ "x${GRUB_FORCE_HIDDEN_MENU}" = "xtrue" ] ; then

[/LIST]


[SIZE=3]**12. [COLOR=DarkRed]HIDING PARTITIONS USING PARTTOOL[/COLOR]**[/SIZE]
Hiding Windows partitions from other Windows installs was a capability in Grub legacy using the "hide" option. In Grub2, this function is now incorporated using the *parttool* module. This section of the guide was the result of a [post 9142327 by GMHilltop]("http://ubuntuforums.org/showpost.php?p=9142327&postcount=4"), who wanted to hide one Windows partition when booting into another one.

The easiest way to incorporate this into the Grub2 menu is through a modification of the /etc/grub.40_custom file. Add the following entries, which should be self-explanatory. If not, GMHilltop provides a bit more explanation in his post.
```

menuentry "Mom & Dads" {
insmod chain
insmod ntfs
parttool (hd0,1) hidden-
parttool (hd0,2) hidden+
parttool (hd0,5) hidden-
set root= (hd0,1)
search --no-floppy --fs-uuid --set 9A7A430F7A42E819
chainloader +1
}

menuentry "Kids Operating System" {
insmod chain
insmod ntfs
parttool (hd0,2) hidden-
parttool (hd0,1) hidden+
parttool (hd0,5) hidden+
set root= (hd0,2)
search --no-floppy --fs-uuid --set 9A18464D18462919
chainloader +1
}

menuentry "Ubuntu" {
parttool (hd0,2) hidden-
parttool (hd0,1) hidden-
parttool (hd0,5) hidden-
parttool (hd0,6) hidden-
recordfail=1
if [ -n ${have_grubenv} ]; then save_env recordfail; fi
set quiet=1
insmod ext2
set root=(hd0,3)
search --no-floppy --fs-uuid --set 9a1e8016-a158-4e98-ae38-6da0fd528d9a
linux /boot/vmlinuz-2.6.31-14-generic root=UUID=9a1e8016-a158-4e98-ae38-6da0fd528d9a ro quiet splash
initrd /boot/initrd.img-2.6.31-14-generic
}

```


[SIZE=3]**13. [COLOR=DarkRed]Removing the Grub 1.99 Submenu[/COLOR]**[/SIZE]
If you want to display all the kernels and eliminate Linux entries from the submenu feature introduced with Grub 1.99, here is how to edit */etc/grub.d/10_linux*. These lines (uncommented) appear at the bottom of the file. **Do not comment the "done" line.**
> 
# if [ "$list" ] && ! $in_submenu; then
# echo "submenu \"Previous Linux versions\" {"
# in_submenu=:
# fi
done

#if $in_submenu; then
# echo "}"
#fi 


[SIZE=3]**14. [COLOR=DarkRed]Troubleshooting[/COLOR]**[/SIZE]
If the tweaks in this section do not work there are several things to check.
[LIST]
[*]Are you working with the correct file? Make sure you are making the changes to the file which deals with the item you are trying to hide. Check the grub.cfg file to see which section the entry is appearing in (10_, 30_, etc).
[*]Is the variable producing the correct result?  The easiest way to check is to either echo the variable results for viewing while update-grub is running or insert the variable in the grub.cfg file for review.
[LIST]
[*]Example: The memtest86+ option keeps appearing in the menu, even though you have inserted "[COLOR=Navy]**nomemtest="`echo ${LLABEL} | cut -d " " -f 1`**[/COLOR]" into 30_os-prober.
[LIST]
[*]Check that the undesired 'memtest86+' menu item is in the 30_os-prober section of grub.cfg
[*]Find out what value 'LLABEL' and 'nomemtest' are returning.
[*]Alter the following line:
```

 cat << EOF
menuentry "**[COLOR=Red]${LLABEL}[/COLOR]** (on ${DEVICE})" {ile allowing os-prob

```to
```

 cat << EOF
nomemtest=${nomemtest} LLABEL=${LLABEL}
menuentry "${LLABEL} (on ${DEVICE}" \

```A sample entry would now look like this, showing you the values:
```

nomemtest=memtest86+ LLABEL=Debian GNU/Linux, kernel memtest86+
menuentry "Debian GNU/Linux, kernel memtest86+" (sda8) {

```Now for each entry, you will have a line directly above displaying the values of nomemtest and LLABEL just before that menu entry was created. With that knowledge, you should be able to tweak the variable to ensure it returns the correct value for the current situation.
[/LIST]
 
[/LIST]
[/LIST]
 

[SIZE=3]**15. [COLOR=DarkRed]CUSTOM MENUS[/COLOR]**[/SIZE]
Grub2 allows the user to place customized menu entries into the main Grub menu via scripts in the */etc/grub.d* folder. One, 40_custom, is prebuilt and items can be added to it's contents. Do not change the existing lines - simply add items below. An easy way to add entries is to copy entries from the */boot/grub/grub.cfg* file and then alter them as desired. 

Note: The scripts in */etc/grub.d* are run, and menu items are placed in the Grub2 menu, sequentially. Naming your /etc/grub.d custom file *06_custom* will place the custom menu entries before those in 10_linux and 30_os-prober. That means they will be placed at the top of GRUB 2's menu. Menu items placed in *40_custom* will appear the bottom of the menu.

If you use a numbered filename less than 30 you may want to check the "DEFAULT=" line in */etc/default/grub* after running *sudo update-grub* to ensure the correct *menuentry* item is identified. 


[LIST=1]
[*] This custom entry is based on *ranch hand*'s post #26. It provides an entry for the latest kernel on the system and will remain current even after a kernel update. UUIDs may be used to identify root if desired.

```

menuentry "Latest Kernel" {
        set root=(hdX,Y)
        linux /vmlinuz root=/dev/sdXY ro quiet splash
        initrd /initrd.img
}

```
[/LIST]
[SIZE=3]**15. [COLOR=DarkRed]POST YOUR TWEAKS![/COLOR]**[/SIZE]

[SIZE=3]Thread Recommendations
[LIST]
[*]Tweaks that only alter the text on the Grub 2 Menu.
[*]If possible, on the first line post the existing title and how it will change.
[/LIST]
[/SIZE]
[LIST]
[*][SIZE=3]**Original Menu Entry: [COLOR=DarkRed]Microsoft Windows XP Home Edition on sda1[/COLOR] >>  New: [COLOR=DarkGreen]XP[/COLOR]**[/SIZE] 

[SIZE=3]To achieve this on the first line, copy/paste the code from the last line of this post and then alter it. [/SIZE]

[noparse]
[size="3"]**Original Menu Entry: [color="DarkRed"]Microsoft Windows XP Home Edition on sda1[/color] >>  New: [color="DarkGreen"]XP[/color]**[/size]
[/noparse][/size]
[/LIST]ery/Single User Entrie

---

### Post by bapoumba on 2009-10-10
Moved to karmic :)

---

### Post by darco on 2009-10-10
Wow, really nice job.....


darco

---

### Post by woodbj on 2009-10-10
Heaps good.. Very Helpful Thanks

---

### Post by ranch hand on 2009-10-10
I surely have not read it all yet but I am subscribed and then I had to read a little.

Looks really good.

---

### Post by woodbj on 2009-10-10
Alright so I have changed the name of the entries so they come up as 

```
Ubuntu karmic Koala
Ubuntu, Linux 2.6.31-13-generic (recovery mode)
Ubuntu karmic Koala
Ubuntu, Linux 2.6.31-12-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Windows Vista
```

But i can't remove the recovery mode kernels or the Memory test options.. 
This is my 30_os-prober
```
#! /bin/sh -e

# grub-mkconfig helper script.
# Copyright (C) 2006,2007,2008,2009  Free Software Foundation, Inc.
#
# GRUB is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# GRUB is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with GRUB.  If not, see <http://www.gnu.org/licenses/>.

prefix=/usr
exec_prefix=${prefix}
libdir=${exec_prefix}/lib

. ${libdir}/grub/grub-mkconfig_lib

found_other_os=

adjust_timeout () {
  if [ "x${found_other_os}" = "x" ] ; then
    if [ "x${GRUB_HIDDEN_TIMEOUT}" != "x" ] ; then
      if [ "x${GRUB_HIDDEN_TIMEOUT_QUIET}" = "xtrue" ] ; then
	verbose=
      else
	verbose=" --verbose"
      fi

      if [ "x${GRUB_HIDDEN_TIMEOUT}" = "x0" ] ; then
	cat <<EOF
if [ \${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep$verbose --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
EOF
      else
	cat << EOF
if [ \${timeout} != -1 ]; then
  if sleep$verbose --interruptible ${GRUB_HIDDEN_TIMEOUT} ; then
    set timeout=0
  fi
fi
EOF
      fi
    fi
  fi
}

if [ "x${GRUB_DISABLE_OS_PROBER}" = "xtrue" ]; then
  adjust_timeout
  exit 0
fi

if [ -z "`which os-prober 2> /dev/null`" -o -z "`which linux-boot-prober 2> /dev/null`" ] ; then
  # missing os-prober and/or linux-boot-prober
  adjust_timeout
  exit 0
fi

OSPROBED="`os-prober | tr ' ' '^' | paste -s -d ' '`"
if [ -z "${OSPROBED}" ] ; then
  # empty os-prober output, nothing doing
  adjust_timeout
  exit 0
fi

for OS in ${OSPROBED} ; do
  DEVICE="`echo ${OS} | cut -d ':' -f 1`"
  LONGNAME="`echo ${OS} | cut -d ':' -f 2 | tr '^' ' '`"
  LABEL="`echo ${OS} | cut -d ':' -f 3 | tr '^' ' '`"
  BOOT="`echo ${OS} | cut -d ':' -f 4`"

  if [ "${LONGNAME}" = "Windows Vista (loader)" ] ; then
    LONGNAME="Windows Vista"
  elif [ -z "${LONGNAME}" ] ; then
    LONGNAME="${LABEL}"
  fi

  echo "Found ${LONGNAME} on ${DEVICE}" >&2
  found_other_os=1

  case ${BOOT} in
    chain)

      cat << EOF
menuentry "${LONGNAME}" {
EOF
      save_default_entry | sed -e "s/^/\t/"
      prepare_grub_to_access_device ${DEVICE} | sed -e "s/^/\t/"

      case ${LONGNAME} in
	Windows\ Vista*|Windows\ 7*)
	;;
	*)
	  cat << EOF
	drivemap -s (hd0) \${root}
EOF
	;;
      esac

      cat <<EOF
	chainloader +1
}
EOF
    ;;
    linux)
      LINUXPROBED="`linux-boot-prober ${DEVICE} 2> /dev/null | tr ' ' '^' | paste -s -d ' '`"

      for LINUX in ${LINUXPROBED} ; do
        LROOT="`echo ${LINUX} | cut -d ':' -f 1`"
        LBOOT="`echo ${LINUX} | cut -d ':' -f 2`"
        LLABEL="`echo ${LINUX} | cut -d ':' -f 3 | tr '^' ' '`"
        LKERNEL="`echo ${LINUX} | cut -d ':' -f 4`"
        LINITRD="`echo ${LINUX} | cut -d ':' -f 5`"
        LPARAMS="`echo ${LINUX} | cut -d ':' -f 6- | tr '^' ' '`"
# User-added variables          
        nomemtest="`echo ${LLABEL} | cut -d " " -f 1`"
        nosingle="`echo ${LPARAMS} | sed 's/^.* //'`"
        hidekernel="`echo ${LKERNEL} | cut -d'-' -f2`"


        if [ -z "${LLABEL}" ] ; then
          LLABEL="${LONGNAME}"
        fi

        if [ ${nomemtest} = "Memory" ] || [ ${nosingle} = "single" ]; then
	   break 
	fi



        cat << EOF
menuentry "${LLABEL}" {
EOF
	save_default_entry | sed -e "s/^/\t/"
	prepare_grub_to_access_device ${DEVICE} | sed -e "s/^/\t/"
	cat <<  EOF
	linux ${LKERNEL} ${LPARAMS}
EOF
        if [ -n "${LINITRD}" ] ; then
          cat << EOF
	initrd ${LINITRD}
EOF
        fi
        cat << EOF
}
EOF
      done
    ;;
    macosx)
      OSXUUID="`grub-probe --target=fs_uuid --device ${DEVICE} 2> /dev/null`"
        cat << EOF
menuentry "${LONGNAME}" {
EOF
	save_default_entry | sed -e "s/^/\t/"
	prepare_grub_to_access_device ${DEVICE} | sed -e "s/^/\t/"
	cat << EOF
        insmod vbe
        do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             do_resume=1
           fi
        fi
        if [ \$do_resume == 0 ]; then
           xnu_uuid ${OSXUUID} uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel /mach_kernel boot-uuid=\${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devtree.txt ]; then
              xnu_devtree /Extra/devtree.txt
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
EOF
    ;;
    hurd|*)
      echo "  ${LONGNAME} is not yet supported by grub-mkconfig." >&2
    ;;
  esac
done

adjust_timeout
```
Would you be able to have a look at it and see if I did something wrong.. thanks

---

### Post by VMC on 2009-10-11
> **woodbj said:**
> But i can't remove the recovery mode kernels or the Memory test options.. 


/etc/grub.d/10_linux:
GRUB_DISABLE_LINUX_RECOVERY=true
also
sudo chmod -x /etc/grub.d/20_memtest86+

---

### Post by autocrosser on 2009-10-11
> **VMC said:**
> /etc/grub.d/10_linux:
GRUB_DISABLE_LINUX_RECOVERY=true
also
sudo chmod -x /etc/grub.d/20_memtest86+


Should the GRUB_DISABLE be added in the: ```
# User-added variable
  **[COLOR=Navy]codename="`lsb_release -cs`"[/COLOR]**
```

---

### Post by drs305 on 2009-10-11
> **autocrosser said:**
> Should the GRUB_DISABLE be added in the: ```
# User-added variable
  **[COLOR=Navy]codename="`lsb_release -cs`"[/COLOR]**
```

The line below should be added to */etc/default/grub* to hide the recovery options. 
```

GRUB_DISABLE_LINUX_RECOVERY="true"

```

You can make the 20_memtest86+ file in etc/grub.d/ non-executable, as was mentioned. This will inhibit the display of the *installed parittion's* memtest86+ option.

It doesn't appear that there is yet a similar entry available in this file to inhibit the display of memtest86+ for *other* partitions, which is the reason the tweak was added in this guide. 

I'll edit the first post in emphasize how to disable memtest86+ and recovery displays in the main partition.

---

### Post by woodbj on 2009-10-11
Thanks Worked like a charm
I uncommented GRUB_DISABLE_LINUX_RECOVERY="true" in /etc/default/grub but that only got rid of the recovery kernels so I also did sudo chmod -x /etc/grub.d/20_memtest86+  and that got rid of the Memtest's.. Thanks again

---

### Post by rburkartjo on 2009-10-11
tks ya'll for making this a sticky

---

### Post by praveenmarkandu on 2009-10-11
excellent thread. i've been waiting for this one. Thanks a bunch

---

### Post by bapoumba on 2009-10-11
Ping drs305 : [http://ubuntuforums.org/showpost.php?p=8087552&postcount=65](http://ubuntuforums.org/showpost.php?p=8087552&postcount=65)
:)

---

### Post by ranch hand on 2009-10-11
Getting a lot of links on my little intro post.

---

### Post by autocrosser on 2009-10-11
> **drs305 said:**
> The line below should be added to */etc/default/grub* to hide the recovery options. 
```

GRUB_DISABLE_LINUX_RECOVERY="true"

```You can make the 20_memtest86+ file in etc/grub.d/ non-executable, as was mentioned. This will inhibit the display of the *installed parittion's* memtest86+ option.

It doesn't appear that there is yet a similar entry available in this file to inhibit the display of memtest86+ for *other* partitions, which is the reason the tweak was added in this guide. 

I'll edit the first post in emphasize how to disable memtest86+ and recovery displays in the main partition.

Thank you--I didn't remember that it was there....

---

### Post by autocrosser on 2009-10-11
Yes--this needs to be a sticky.

---

### Post by drs305 on 2009-10-11
> **autocrosser said:**
> Thank you--I didn't remember that it was there....

I suspect there are a wide range of lines we don't yet know about. I seem to stumble on at least one a week. Eventually most of this thread will probably be eliminated as easier ways to incorporate the changes become known.  ;-)

---

### Post by autocrosser on 2009-10-11
Yes---I'm waiting for SUM to get the abilities to do this stuff--I've talked to the developer in the past, maybe I'll drop him a line again to see how it is coming along.......

---

### Post by scradock on 2009-10-11
> **drs305 said:**
> I suspect there are a wide range of lines we don't yet know about. I seem to stumble on at least one a week. Eventually most of this thread will probably be eliminated as easier ways to incorporate the changes become known.  ;-)
For instance, an easier way (at least for me) to remove the memtest lines for OTHER linux installs is to delete the memtest stanzas from the respective /boot/grub/menu.lst files. It appears that GRUB2 gets a lot of its information (using osprober) by reading it out of any appropriate menu.lst files it can find.

Hope that helps.....

---

### Post by drs305 on 2009-10-12
> **scradock said:**
> For instance, an easier way (at least for me) to remove the memtest lines for OTHER linux installs is to delete the memtest stanzas from the respective /boot/grub/menu.lst files. It appears that GRUB2 gets a lot of its information (using osprober) by reading it out of any appropriate menu.lst files it can find.

Hope that helps.....

scradock,

Nice info! 

The advantage of your method is that users are, at least for now, still familiar with the menu.lst file and how to edit it. I placed comments (#) on the memtest86+ lines in the one old menu.lst I have on my system. The memtest option for that partition disappeared just as you said it would as soon as I ran update-grub. :-)

The advantage of placing something in the script is that it won't change, and for multiple installs you only have to do it in one place instead of rooting out each menu.lst. It also would account for memtest entries in partitions without a Grub legacy menu.lst.

Your post might help solve another thing that has 'ranch hand' and I puzzled - the appearance of a "(memtest86+, serial console 115200)" entry. I only have one extra linux partition with a menu.lst entry. I'm wondering if a second menu.lst might generate such a designation...

Thanks again for the input.

---

### Post by scradock on 2009-10-12
The memtest line with 115200 in it is explicitly inserted by 20_memtest86+. I guess it's another option the dev decided to make available.

We could comment it out, but that would only work until the next upgrade. I don't think any fancy script stuff is needed.

---

### Post by Evil Dax on 2009-10-18
Hi, nice how-to!

1 question:
My GRUB loads 2x Windows Vista:
Windows Vista (loader) (on /dev/sda1)
Windows Vista (loader) (on /dev/sda2)

From which the 1st is the recovery partition, and the second the working one.

Changing the filename from the how-to changes them both (is the same name)

Is there a quick way to rename 1 to 'rescue' and leave the other one to 'loader'?

---

### Post by drs305 on 2009-10-18
> **Evil Dax said:**
> Hi, nice how-to!

1 question:
My GRUB loads 2x Windows Vista:
Windows Vista (loader) (on /dev/sda1)
Windows Vista (loader) (on /dev/sda2)

From which the 1st is the recovery partition, and the second the working one.

Changing the filename from the how-to changes them both (is the same name)

Is there a quick way to rename 1 to 'rescue' and leave the other one to 'loader'?

Evil Dax,

Let me state outright that my knowledge of scripting is very limited. However, what you want should be easily attained by combining two conditionals.

From the Windows section:
> 
  if [ "${LONGNAME}" = "Enter Exact Title You Just Copied" ] ; then
    LONGNAME="Enter Desired New Title Here"
  elif [ -z "${LONGNAME}" ] ; then
    LONGNAME="${LABEL}"
  fi

You would alter the first line to include a second condition, that being that ${DEVICE} is equal to either sda1 (or sda2). 

So the conditional statement would be:

Added:  Stop the presses: go to post #31 for the formula he successfully used...

> 
  if [[ "${LONGNAME}" = "Enter Exact Title You Just Copied" &&  "${DEVICE}" = "/dev/sda1" ]] ; then
    LONGNAME="Enter Desired New Title Here"
  elif [ -z "${LONGNAME}" ] ; then
    LONGNAME="${LABEL}"
  fi

The syntax may not be exactly right (I don't have the time to look it up at the moment) but you should get the idea. You would have to work out something for the other OS as well, another "elif" for instance.

---

### Post by Eddie Wilson on 2009-10-18
Here is a nice one for somebody. I've been working with Grub 2 and I'm starting to get the hang of it but I do have a question. I also have Kubuntu installed. I would always edit the menu.lst to change Ubuntu to Kubuntu but now it does not seem to keep the Kubuntu title whenever I update Kubuntu or Ubuntu. Is there anyway at this time to keep the Kubuntu title?

Also, nice thread.

---

### Post by drs305 on 2009-10-19
> **Eddie Wilson said:**
> I would always edit the menu.lst to change Ubuntu to Kubuntu but now it does not seem to keep the Kubuntu title whenever I update Kubuntu or Ubuntu. Is there anyway at this time to keep the Kubuntu title?

Eddie, 

I tried the "lsb_release -a" command but it returns "Ubuntu". If there is a command that returns a value of "Kubuntu" a variable could easily be added into 10_linux. 

If you don't have *any* Ubuntu releases that you want to see, you could change all the Ubuntu listings to "Kubuntu". Again, this isn't elegant, but it would work. It looks for any {OS} named "Ubuntu" and replaces it with variable *newname*, which is "Kubuntu".

Make a backup of 10_linux first: sudo cp /etc/grub.d/10_linux /etc/grub.d/10_linux && sudo chmod -x /etc/grub.d/10_linux

In /etc/grub.d/10_linux, around line 115:

> 
[B]if [ ${OS}="Ubuntu" ] ; then
    newname="Kubuntu"
fi[/B]

  linux_entry "**$newname** ${version}" \
      "${GRUB_CMDLINE_LINUX} ${GRUB_CMDLINE_EXTRA} ${GRUB_CMDLINE_LINUX_DEFAULT}" \
      quiet
  if [ "x${GRUB_DISABLE_LINUX_RECOVERY}" != "xtrue" ]; then
    linux_entry "**$newname**, Linux ${version} (recovery mode)" \
	"single ${GRUB_CMDLINE_LINUX}"
  fi


A less desirable option would be to create an "06_custom" file and put the entry in manually, but that menu wouldn't be updated automatically. 

Perhaps someone will provide a command or another solution.

---

### Post by ranch hand on 2009-10-19
I would use the 06_custom file route.  By using this entry, suitably edited to your partition, you will NEVER have to update, it will boot the newest kernel on the partition;
```

echo "Kubuntu 9.10 on sda22" >&2
cat << EOF
menuentry "Kubuntu 9.10 on sda22" {
        set root=(hd0,22)
        linux /vmlinuz root=/dev/sda22 so quiet splash
        initrd /initrd.img
}
EOF

```

---

### Post by VMC on 2009-10-19
> **ranch hand said:**
> I would use the 06_custom file route.  By using this entry, suitably edited to your partition, you will NEVER have to update, it will boot the newest kernel on the partition;
```

echo "Kubuntu 9.10 on sda22" >&2
cat << EOF
menuentry "Kubuntu 9.10 on sda22" {
        set root=(hd0,22)
        linux /vmlinuz root=/dev/sda22 so quiet splash
        initrd /initrd.img
}
EOF

```

I also prefer this method now too. I wish Fedora and the rest of Linux distro's would follow suite. Makes it very convenient.

---

### Post by drs305 on 2009-10-19
> **VMC said:**
> I also prefer this method now too. I wish Fedora and the rest of Linux distro's would follow suite. Makes it very convenient.

 I like it too. In fact, I'm going to add a section to the original post for Custom Menu tweaks. This will be the first one - with attribution of course!  ;-)

---

### Post by ranch hand on 2009-10-19
> **drs305 said:**
> I like it too. In fact, I'm going to add a section to the original post for Custom Menu tweaks. This will be the first one - with attribution of course!  ;-)
See Hermans bit on menu entries.  That is the best explaination I have found.  It sure is handy.

I have change OS' on a set of partitions and not had to change the entry.  I did go back and change the buggers, the titles were not right any more, but that doesn't stop it from booting to the partition.  It is cool, I love it.

---

### Post by drs305 on 2009-10-19
> **ranch hand said:**
> See Hermans bit on menu entries.  That is the best explaination I have found.  It sure is handy.

I visit his site often. It's a great resource and I've linked it on my main Grub 2 thread. Since I don't have a "Links" section on this page (at least not yet), here it is.


[http://members.iinet.net/~herman546/p20.html]("http://members.iinet.net/~herman546/p20.html")

Worthwhile reading for anyone interested in bootloaders. Well, maybe that isn't the best choice of words, but an incredible amount of information if you want to learn more or are having problems booting.

---

### Post by Evil Dax on 2009-10-20
Thanks drs305, got it working now:
your code was almost right, and got me on the way:

```

if [[ "${LONGNAME}" = "Enter Exact Title You Just Copied" && "${DEVICE}" = "/dev/sda1" ]] ; then
LONGNAME="Enter Desired New Title Here"
elif [ -z "${LONGNAME}" ] ; then
LONGNAME="${LABEL}"
fi 

```

should be:
```

if [ "${LONGNAME}" = "Enter Exact Title You Just Copied" ] && [ "${DEVICE}" = "/dev/sda1" ] ; then
LONGNAME="Enter Desired New Title Here"
elif [ -z "${LONGNAME}" ] ; then
LONGNAME="${LABEL}"
fi
 
```

(just a different use of the [  ] items.)

Thanks!

Dax

---

### Post by negativ on 2009-10-24
This looks helpful; maybe I will try again.  On the other hand, it perfectly illustrates what a bloated pile of failure GRUB2 is. The HOWTO for changing the GRUB2 boot menu is almost as long as the HOWTO for setting up a LAMP server, and that is desperately sad.

---

### Post by alveola on 2009-11-15
Thanks for this (and other) postings about grub2. I had a bit of trouble with some of the code, to be exact: part 2D. The string comparison gave me some errors. The solution was to quote both the parts before and after the equal sign. For this part it would be as follows:

(it's hard to see, but the changes (double quotes) are **_bold and underlined_**):

```
        if [ **_"_**${nomemtest}**_"_** = "Memory" ] || [ **_"_**${nosingle}**_"_** = "single" ]; then
       continue 
    fi

```

btw: I found the solution here:
[http://stackoverflow.com/questions/1089813/bash-dash-and-string-comparison](http://stackoverflow.com/questions/1089813/bash-dash-and-string-comparison)

---

### Post by drs305 on 2009-11-15
> **alveola said:**
> Thanks for this (and other) postings about grub2. I had a bit of trouble with some of the code, to be exact: part 2D. The string comparison gave me some errors. The solution was to quote both the parts before and after the equal sign. 

Ok, thanks. I'm at a hotel so I'll change them now and play with them when I return home.

---

### Post by deep64blue on 2009-11-20
I'm trying to remove the (on /dev/sda2) string this brain dead piece of crap keeps adding but I searched 10_linux for the string ${DEVICE} and didn't find it. Any ideas?

---

### Post by drs305 on 2009-11-20
> **deep64blue said:**
> I'm trying to remove the (on /dev/sda2) string this brain dead piece of crap keeps adding but I searched 10_linux for the string ${DEVICE} and didn't find it. Any ideas?

The 10_linux script works on the system partition and doesn't attach the "(on /dev/sda4)" label to the menuentry.  

Most likely, you have another Linux installation on a different partition that is being detected by 30_os-prober. You can check by looking at /boot/grub/grub.cfg. The contents of this file are sectioned by the script that created it ("### BEGIN.... ). Find the menuentry which you want to change and then determine the section it is in. The section name is the same as the file you want to edit.

---

### Post by burgerearl on 2009-11-23
Wow, thanks for the great writeup. I'm a total newbie and I could follow it no problem!

This is perhaps trivial, but 
```
codename="`lsb_release -cs`"
```

returns the codename in all lowercase. Would it be ridiculous to make it capitalize the first letter?

Another very particular question:

Would it be possible to use only the last part of the kernel version number to, for example, get an entry to read like "Ubuntu Karmic (-14)"

---

### Post by drs305 on 2009-11-23
> **burgerearl said:**
> 
This is perhaps trivial, but 
```
codename="`lsb_release -cs`"
```
returns the codename in all lowercase. Would it be ridiculous to make it capitalize the first letter?


Hey, I *said* this thread was for truly anal users, so all ridiculous is accepted!  ;-)

I worked with the 10-linux file, although you could modify them for use in the 30_os-prober file as well. I am referencing Section 1 of the first post. Under **[COLOR="Navy"] codename="`lsb_release -cs`"[/COLOR]** add this line:
> **[COLOR="Navy"]Codename="`echo $codename | tr [hjkl] [HJKL]`"[/COLOR]**
It's a hack, but will translate hardy/jaunty/karmic/lucid into Hardy/Jaunty/Karmic/Lucid.  There is obviously a better script, but this is simple and will work specifically for those names. Note you couldn't add an *I* for intrepid, since it would turn out IntrepId...

> 
Another very particular question:

Would it be possible to use only the last part of the kernel version number to, for example, get an entry to read like "Ubuntu Karmic (-14)"

To shorten to just the trailing digits (example -14), add this variable in the same place:
> **[COLOR="Navy"]short_version="(-`echo $version | cut -d "-" -f 2`)"[/COLOR]**
If you want to see "-14-generic" use this:
> **[COLOR="Navy"]short_version="(-`echo $version | cut -d "-" -f 2-`)"[/COLOR]**

Then change the original line:
> linux_entry "${OS}, Linux ${version}" \

to:
> **[COLOR="Navy"]linux_entry "${Codename} ${shortversion}" \[/COLOR]**


Combined, the two should produce results like these:
[COLOR="DarkRed"]**Karmic (-14)**[/COLOR]
[COLOR="DarkRed"]**Karmic (-14-generic)**[/COLOR]

---

### Post by burgerearl on 2009-11-24
Perfect, that did exactly what I wanted. Thanks!

To reduce my newbliness, what would this be called? Just scripting language, or....? Basically, I'm wondering what I should search for to teach myself some of the syntax.

---

### Post by drs305 on 2009-11-24
> **burgerearl said:**
> Perfect, that did exactly what I wanted. Thanks!

To reduce my newbliness, what would this be called? Just scripting language, or....? Basically, I'm wondering what I should search for to teach myself some of the syntax.

If you look at the first line of the script files you will see most are bash. Some are sh. Everything I've tweaked has been with basic BASH scripting, and I'm talking *very* basic BASH. More complex BASH statements could be used in many of the examples but I've kept most of the tweaks simple.

There are lots of BASH examples and tutorials floating around the internet.

---

### Post by Antonello Amici on 2009-12-04
for capitalize the first letter of codename

```
codename=`lsb_release -cs | sed "s/^./\u&/"`
```

;)

---

### Post by ShadowMage on 2009-12-07
Hey all,

This thread helped me customize my grub2 menu and I thank you all for that. I just thought I'd share with you guys something that is not found here. I mentioned it in the thread I created [[COLOR=Blue]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1324728"), but I think it's more useful if I post it here.

Okay so first, note that this is for the **system partition** (i.e. the *10_linux* file). I wanted the version number of Ubuntu to show up. Using lsb_release in a different way from the codename variable this thread already introduces, I instead introduced the following variable
```
  ## User-added variables
  description="`lsb_release -ds`"
  ##
```which in my case evaluates to the string "Ubuntu 9.10".

Cheers.

---

### Post by LaZaNha on 2009-12-28
first, thx for the great tutorial, used many parts of it and it worked like a charm

i`m just breaking my head while trying to hide a kernel version from showing

this is what grub is currently displying

Ubuntu 9.10 (Karmic) 2.6.31-16-generic
Ubuntu 9.10 (Karmic) 2.6.31-14-generic
Windows 7 Professional

And i want to hide Ubuntu 9.10 (Karmic) 2.6.31-14-generic

the following code was extrated from the linux part of 30_os-prober, where i made the sugested changes to hide it

```
      for LINUX in ${LINUXPROBED} ; do
        LROOT="`echo ${LINUX} | cut -d ':' -f 1`"
        LBOOT="`echo ${LINUX} | cut -d ':' -f 2`"
        LLABEL="`echo ${LINUX} | cut -d ':' -f 3 | tr '^' ' '`"
        LKERNEL="`echo ${LINUX} | cut -d ':' -f 4`"
        LINITRD="`echo ${LINUX} | cut -d ':' -f 5`"
        LPARAMS="`echo ${LINUX} | cut -d ':' -f 6- | tr '^' ' '`"
	hidekernel="`echo ${LKERNEL} | cut -d'-' -f2-3`"

        if [ -z "${LLABEL}" ] ; then
          LLABEL="${LONGNAME}"
        fi

 	if [ ${hidekernel} = "2.6.31-14" ]; then
       continue
    	fi

         if [ "${LROOT}" != "${LBOOT}" ]; then
           LKERNEL="${LKERNEL#/boot}"
           LINITRD="${LINITRD#/boot}"
         fi

        cat << EOF
```

but its not working

tried if [ ${hidekernel} = "2.6.31-14-generic" ] and still no good

any suggestions??

thank you very much

---

### Post by drs305 on 2009-12-28
> **LaZaNha said:**
> first, thx for the great tutorial, used many parts of it and it worked like a charm

i`m just breaking my head while trying to hide a kernel version from showing

this is what grub is currently displying

Ubuntu 9.10 (Karmic) 2.6.31-16-generic
Ubuntu 9.10 (Karmic) 2.6.31-14-generic
Windows 7 Professional

And i want to hide Ubuntu 9.10 (Karmic) 2.6.31-14-generic

**the following code was extrated from the linux part of 30_os-prober, where i made the sugested changes to hide it**


tried if [ ${hidekernel} = "2.6.31-14-generic" ] and still no good

any suggestions??

thank you very much

Are the kernels you want to hide on a different partition? It appears these are part of your normal installation. If you want to hide *2.6.31-14-generic* on your normal install you would modify the 10_linux file and not the 30_os-prober file, which looks for OS's on other partitions.

One thing I do when I experiment with these tweaks and they don't work is to take a step back to see what the result of the "uncut" variable is, such as "hidekernel" and "LKERNEL" to make sure I am working with the correct starting point. In this case, I would add the following lines just after the variable definitions and on a line just put "echo ${LKERNEL}" and on the next "echo $hidekernel" (without the quotes). Then run the update-grub command and check the 30_os-prober section of /boot/grub/grub.cfg to see what those two variables are producing. Of course, remove these lines and run the update again before rebooting.

If you still are having problems hiding the kernel come back and let us know.

---

### Post by LaZaNha on 2009-12-29
drs305, you were right!

i didn`t realize that i was messing with the wrong file.

but even after that i struggled a little bit to get it to work.

finally, the following code inserted after variable version was declared in 10_linux made it work

```
    if [ ${version} = "2.6.31-14-generic" ]; then
       break
    fi
```

thanks for the help!! i promise im gonna study shell script from now on hahahaa :)

---

### Post by drs305 on 2009-12-29
> **LaZaNha said:**
> drs305, you were right!

i didn`t realize that i was messing with the wrong file.

but even after that i struggled a little bit to get it to work.

finally, the following code inserted after variable version was declared in 10_linux made it work

```
    if [ ${version} = "2.6.31-14-generic" ]; then
       break
    fi
```

thanks for the help!! i promise im gonna study shell script from now on hahahaa :)

I just reviewed the opening post and realized that my examples didn't include one for hiding specific kernels on the main partition. Thanks for your input.

Below is an alternate method of hiding -14. Your entry will hide the -14 kernel, but it would also prevent any kernel number lower than -14 from displaying because the script would stop as soon as it found -14. So if you wanted to see -12, it wouldn't end up in the menu.

A different approach would be to alter the 10_linux script in this manner. The [COLOR="DarkGreen"]dark green lines[/COLOR] are added to the script.
> 
[COLOR="DarkGreen"]**if [ ${version} != "2.6.31-14-generic" ]; then**[/COLOR]
  linux_entry "${OS}, Linux ${version}" \
      "${GRUB_CMDLINE_LINUX} ${GRUB_CMDLINE_EXTRA} ${GRUB_CMDLINE_LINUX_DEFAULT}" \
      quiet
  if [ "x${GRUB_DISABLE_LINUX_RECOVERY}" != "xtrue" ]; then
    linux_entry "${OS}, Linux ${version} (recovery mode)" \
    "single ${GRUB_CMDLINE_LINUX}"
  fi
[COLOR="DarkGreen"]**fi**[/COLOR]

The first line tells the script that if the kernel is not -14, continue. If it is -14, entry into the menu will be skipped. This way the -12 kernel, if present, would still show up on the menu.

Of course, if you didn't want to display -14 *or earlier*, your way would work. Or you can always remove the -14 kernel via Synaptic and be done with it!  There are many ways to do things in Linux, which is one of the reasons I like it so much.

Again, thanks for your contribution.

---

### Post by jmine83 on 2010-01-23
I am trying to hide/remove the entry in my GRUB 2 loader menu that is for the Windows Vista recovery partition. I did see the instructions on how to do this in the initial post of this thread, but it's not working for some reason. As far as the "exact" name and location of the partition, mine is precisely identical to what was described in the instructions, so I did not mess with this because I do not believe it's the problem.

What I suspect the problem "is", is that the sample code in the instructions was not properly formatted to demonstrate "exactly" how the code should be written, "including" the amount of tab space from the left. Here is the code I have in my "30_os-prober" file, starting at line 83:

```

for OS in ${OSPROBED} ; do
  DEVICE="`echo ${OS} | cut -d ':' -f 1`"
  LONGNAME="`echo ${OS} | cut -d ':' -f 2 | tr '^' ' '`"
  LABEL="`echo ${OS} | cut -d ':' -f 3 | tr '^' ' '`"
  BOOT="`echo ${OS} | cut -d ':' -f 4`"

  if [ -z "${LONGNAME}" ] ; then
    LONGNAME="${LABEL}"
  fi

  if [ "$LONGNAME" = "Windows Vista (loader)" ] && [ "${DEVICE}" = "/dev/sda1" ] ; then
    continue 
  fi

```

Now, in the last "if" statement loop described that was specified in the instructions, is where the problem is. When I go to run the "update-grub" command from command line prompt, I get the following error message:

: not found/30_os-prober: 217: continue

I have played around with the specific line of code you wrote to hide the windows recovery partition, and what I have found is that whatever text string I type in on the same line as "continue" will reflect the same in the end of the error code listed above.

Please let me know what I need to do to get this windows recovery partition mod working.

---

### Post by drs305 on 2010-01-23
jmine83,

Welcome to Ubuntu and the Ubuntu forums. I'd be glad to help you out but we'll need to see the full /etc/grub.d/30_os-prober and /boot/grub/grub.cfg files so I can compare line numbers, titles, etc. You can just attach them to your previous post if you like. To ensure we have *everything*, you could also attach the results of the ever-popular "boot info script". Here are the [instructions]("http://ubuntuforums.org/showpost.php?p=6725571").

Added:
I just cut/pasted the text in the original post, changing only the title since I don't have Vista. It worked as depicted, hiding the partition. Note I don't have tabs/spaces before or after "continue". 

If you would like to experiment a bit further, you can hide the recovery partition by just designating the *device*. 
> 
 if [ "${DEVICE}" = "/dev/sda1" ] ; then
    continue
  fi


---

### Post by jmine83 on 2010-01-27
drs305,

Thank you kindly for your response and input to my prior post. Attached to this post, you will find a .tar file which has three files enclosed within it as per your instructions requested. Again, I am simply trying to hide the Windows Vista recovery partition so that in the end, my GRUB menu only shows two choices: Windows 7 and Ubuntu.

---

### Post by drs305 on 2010-01-27
> **jmine83 said:**
> drs305,

Thank you kindly for your response and input to my prior post. Attached to this post, you will find a .tar file which has three files enclosed within it as per your instructions requested. Again, I am simply trying to hide the Windows Vista recovery partition so that in the end, my GRUB menu only shows two choices: Windows 7 and Ubuntu.

Do you have your original grub files? It appears you renamed some standard files with non-standard names. While you can certainly *have* a these filenames and they will work, it may confuse things.

I will set up a 30_os-prober file for you later today and post it in this thread. I'll be using the 1.97beta standard version of Grub 2 which is what you should see in the Grub 2 menu when you boot. In the meantime, if you created them by what you thought were instructions in my guide, delete 10_os-prober and 20_linux. The standard files in /etc/grub.d are 00_header, 05_debian_theme, 10_linux, 20_memtest86+, 30_os-prober, 40_custom and README.

---

### Post by drs305 on 2010-01-27
jmine83,

After you restored the original Grub 2 files to the /etc/grub.d folder, rename /etc/grub.d/30_os-prober file: 

```
sudo mv /etc/grub.d/30_os-prober  /etc/grub.d/30_os-prober.original
```

If the attached archive is on your Desktop, you can run these commands to extract the files, copy 30_os-prober to /etc/grub.d and make sure it is executable. A copy of the original will remain on your desktop.
```

sudo tar -x 30_os-prober.tar.bz2 
sudo cp ~/Desktop/30_os-prober /etc/grub.d/
sudo chmod +x /etc/grub.d/30_os-prober
```

The lines added to 30_os-prober are lines 96-100. They will prevent any detected OS/kernel/etc on "sda1" from appearing in your Grub 2 menu.

---

### Post by meierfra. on 2010-01-27
>  not found/30_os-prober: 217: continue


Did you edit 10_os-prober from Windows?

 I downloaded your 10_os-prober file, placed in  my "/etc/grub.d" and run "update-grub". I got the same error message. I then opened "10_os-prober" in emacs and  noticed  a "^M" at the end of the "continue" statement.  "^M" is a Dos style line break.   I removed the "^M".  Now  "update-grub"  completed without error.

So if you edit a Grub 2 configuration file, you need to make sure that you use an editor which uses unix line breaks.

---

### Post by jmine83 on 2010-01-27
> **meierfra. said:**
> Did you edit 10_os-prober from Windows?

 I downloaded your 10_os-prober file, placed in  my "/etc/grub.d" and run "update-grub". I got the same error message. I then opened "10_os-prober" in emacs and  noticed  a "^M" at the end of the "continue" statement.  "^M" is a Dos style line break.   I removed the "^M".  Now  "update-grub"  completed without error.

So if you edit a Grub 2 configuration file, you need to make sure that you use an editor which uses unix line breaks.

Nice :D that was it. I did use gedit in Ubuntu to edit the file, so I am glad you caught that. I edited the file with emacs as you mentioned, saw the "^M" character you noted, ran "update-grub" and that did it. Thank you very much.

---

### Post by meierfra. on 2010-01-27
> I did use gedit in Ubuntu to edit the file, 
That's weird. I would be  surprised if it problem was really caused by Gedit. 
> Nice  that was it. 
Great. I enjoyed solving this little puzzle.

---

### Post by djg5211 on 2010-01-28
Greetings! ):P

Does anyone know how to set the menu FONT SIZE?

Thanks!
Dave :biggrin:

---

### Post by drs305 on 2010-01-28
> **djg5211 said:**
> Greetings! ):P

Does anyone know how to set the menu FONT SIZE?

Thanks!
Dave :biggrin:

The Grub 2 menu font size can be indirectly set with the /etc/default/grub line - in that the screen resolution set by this line will effect how large the fonts are on the standard Grub 2 menu. You can see the available resolutions by typing "c" while the Grub 2 menu is displayed and typing "vbeinfo" without the quotes. :

> GRUB_GFXMODE=640x480

If you want to directly set the font-size via a font command, I don't think that is yet possible in 1.97beta.

---

### Post by djg5211 on 2010-01-28
> **drs305 said:**
> The Grub 2 menu font size can be indirectly set with the /etc/default/grub line - in that the screen resolution set by this line will effect how large the fonts are on the standard Grub 2 menu. You can see the available resolutions by typing "c" while the Grub 2 menu is displayed and typing "vbeinfo" without the quotes. :



If you want to directly set the font-size via a font command, I don't think that is yet possible in 1.97beta.

drs305,

 Hey! Thanks for the response! I understand what you are saying and will
try that. It just seemed a bit odd that there are all of those fonts
there but no way to adjust SIZE? I got the font color thing figured
out and the progress bar the color i wanted it.... now if the font
size thing works i'll be set.

Thanks Again!
Dave

---

### Post by drs305 on 2010-01-28
> **djg5211 said:**
> drs305,

 Hey! Thanks for the response! .... now if the font
size thing works i'll be set.

Thanks Again!
Dave

I love optimism.  ;-)  

But what will happen next is: If you have a Grub 2 splash image, you are going to have to resize it to the same proportions as your new resolution or it won't appear correctly (if at all). 

Theming is coming along in Grub 2 and BURG probably already has the capabilities you are looking for. That is where a lot of the font tweaking will probably become available.  

Note Added: BURG is not Grub. Discussing the differences is beyond the scope of this thread.

---

### Post by djg5211 on 2010-01-29
Hey Y'all...

The stuff below came from another thread by Bean123 regarding
burg (since you mentioned it re:font settings). Just thought
it might be useful to someone else??? ;)
--------------------------------------

First you need to open /boot/burg/fonts/font.lst to see what fonts are available, then you can replace the font parameter, for example "Fixed Regular 20".

You can use burg-mkfont to generate new fonts, -h option to show all options, for example:

Code:

burg-mkfont -o my_font.pf2 -s 20 my_font.bdf

You can also convert TTF.

Then, copy my_font.pf2 to /boot/burg/fonts, and use the following command to update the font list:

Code:

cd /boot/burg/fonts
sudo burg-mkfont -i *.pf2 > font.lst

-----------------------
Thanks Again Again!!! :biggrin::biggrin:
Dave

---

### Post by daodeltaforce on 2010-02-13
I am using Kubuntu 9.10. What is the script to change /etc/grub.d/10_linux from default linux kernel menu to show instead "Kubuntu 9.10 Karmic Koala". Thanks.

---

### Post by drs305 on 2010-02-13
> **daodeltaforce said:**
> I am using Kubuntu 9.10. What is the script to change /etc/grub.d/10_linux from default linux kernel menu to show instead "Kubuntu 9.10 Karmic Koala". Thanks.

daodeltaforce,

See if posts 25 or 26 meets your needs.

---

### Post by bforbes on 2010-02-14
I don't want the GRUB menu to display, so I set hidden_timeout to zero, and the line is uncommented. However, I still get the menu every boot without pressing a key. I disabled os-prober, updated, still getting the menu. What else can I try?

PS: The menu entries are regular and recovery options for two kernels, and memtest.

---

### Post by daodeltaforce on 2010-02-14
Thanks drs305.

Since I am using only kubuntu, I modified 10_linux with newname variable, and it worked fine.

[B]if [ ${OS}="Ubuntu" ] ; then
    newname="Kubuntu 9.10 Karmic Koala"
fi[/B]

  linux_entry "**$newname** ${version}" \
      "${GRUB_CMDLINE_LINUX} ${GRUB_CMDLINE_EXTRA} ${GRUB_CMDLINE_LINUX_DEFAULT}" \
      quiet
  if [ "x${GRUB_DISABLE_LINUX_RECOVERY}" != "xtrue" ]; then
    linux_entry "**$newname**, Linux ${version} (recovery mode)" \
    "single ${GRUB_CMDLINE_LINUX}"
  fi

---

### Post by bforbes on 2010-02-14
The new tweak for hiding the menu with multiple OSes worked perfectly for me, thanks. I'm a bit confused though; I had disabled the os-prober script; why was I still seeing the menu, if the problem originated in code from the os-prober script?

---

### Post by drs305 on 2010-02-14
> **bforbes said:**
> The new tweak for hiding the menu with multiple OSes worked perfectly for me, thanks. I'm a bit confused though; I had disabled the os-prober script; why was I still seeing the menu, if the problem originated in code from the os-prober script?


That was quick. I just added the "hidden menu" tweak a short while ago.

The design is that you are going to see the menu, whether or not 30_os-prober is active. Grub 2 wants to provide the menu if there are any problems detected or if certain conditions aren't met, so hiding the menu is the exception. There are multiple checks throughout the scripts to check for various failures. About the only time that isn't true is if there is only one OS and everything seems correct to Grub 2.

The tweak is that *hiding* the menu is also in the 30_os.. file, and the hidden menu conditional is originally only activated if there no other OS's are found on the system. The tweak says to disregard whether there are multiple OS's or not.

I am not sure why it was put in 30_os-prober, as is the keystatus check. Both to me shouldn't be restricted to running only in the 30 file but that's the way they did it.

I didn't mention it, but you do have to have the 30_ file executable for the hidden menu to work, but most users would have that script active if they have multiple OSs. Someone who had built and relied only on a custom script wouldn't get the tweak to work if they had disabled 30_, but then, would they really want to hide their handiwork?  ;-)

---

### Post by CharlesA on 2010-03-14
Hi there,

I was wondering if it's possible to display the kernel, but leave off the "-generic" part.

Thanks!

---

### Post by drs305 on 2010-03-14
> **CharlesA said:**
> I was wondering if it's possible to display the kernel, but leave off the "-generic" part.

Charles,

For linux kernels on your main partition, open up /etc/grub.d/10_linux:
```
gksu gedit +115 /etc/grub.d/10_linux
```

Find this section around line 95 and add the portion in [COLOR="DarkRed"]**bold dark red**[/COLOR]:
> while [ "x$list" != "x" ] ; do
  linux=`version_find_latest $list`
  echo "Found linux image: $linux" >&2
  basename=`basename $linux`
  dirname=`dirname $linux`
  rel_dirname=`make_system_path_relative_to_its_root $dirname`
  version=`echo $basename | sed -e "s,^[^0-9]*-,,g"`
  alt_version=`echo $version | sed -e "s,\.old$,,g"`
  linux_root_device_thisversion="${LINUX_ROOT_DEVICE}"
[COLOR="DarkRed"]**version_without_generic="`echo $version  | cut -d "-" -f 1-2`"**[/COLOR]

Next change the lines at approximately 115 and 120:
From:
>   linux_entry "${OS}, Linux ${version}" \
To:
>   linux_entry "${OS}, Linux ${[COLOR="DarkRed"]**version_without_generic**[/COLOR]}" \

From:
>    linux_entry "${OS}, Linux ${version} (recovery mode)" \

To:
>    linux_entry "${OS}, Linux ${[COLOR="DarkRed"]**version_without_generic**[/COLOR]} (recovery mode)" \


Finally, update grub and watch for any errors in the terminal as the command generates a new grub.cfg file. If it does generate an error let me know:
```
sudo update-grub
```

I'll try to add this to the examples in the first post later today.

---

### Post by CharlesA on 2010-03-14
Thank you! I'll give it a shot. Great job with the research and whatnot. Grub2 is a major pain in the butt compared to legacy grub.

---

### Post by CharlesA on 2010-03-15
That worked, but it also cut off the "-14" part. I don't think it's possible to keep that one *and* remove the "-generic" part, since the delimiter is a "-"

Anyway, the line I used looks like this:

```
version_without_generic="(`echo $version | cut -d "-" -f1`)"
```

And the result was (I didn't change the name yet):

```
Ubuntu, Linux (2.6.31)
Ubuntu, Linux (2.6.31) (recovery mode)

```

It looks much cleaner now. Thanks again!

---

### Post by drs305 on 2010-03-15
> **CharlesA said:**
> That worked, but it also cut off the "-14" part. 

It looks much cleaner now. Thanks again!


Change it to 
> version_without_generic="`echo $version | cut -d "-" -f 1-2`"

You really should have that portion of the kernel displayed.

I've revised the previous post. I put it in the original post as "-f 1-2" but apparently dropped it here.

---

### Post by CharlesA on 2010-03-15
Thanks! That did the trick.

---

### Post by tad1073 on 2010-03-15
> **daodeltaforce said:**
> Thanks drs305.

Since I am using only kubuntu, I modified 10_linux with newname variable, and it worked fine.

[B]if [ ${OS}="Ubuntu" ] ; then
    newname="Kubuntu 9.10 Karmic Koala"
fi[/B]

  linux_entry "**$newname** ${version}" \
      "${GRUB_CMDLINE_LINUX} ${GRUB_CMDLINE_EXTRA} ${GRUB_CMDLINE_LINUX_DEFAULT}" \
      quiet
  if [ "x${GRUB_DISABLE_LINUX_RECOVERY}" != "xtrue" ]; then
    linux_entry "**$newname**, Linux ${version} (recovery mode)" \
    "single ${GRUB_CMDLINE_LINUX}"
  fi

Do you know about what line that entry is on?

Never mind, I found it.

---

### Post by tad1073 on 2010-03-16
Do I need to remove "false" from the end of that line?

```
@Line 143 # "UUID=" magic is parsed by initrds.  Since there's no initrd, it can't work here.
    linux_root_device_thisversion=${GRUB_DEVICE}
  fi

  linux_entry "${OS}" "${version_no_generic}" [COLOR=Red]**false**[/COLOR] \
      "${GRUB_CMDLINE_LINUX} ${GRUB_CMDLINE_EXTRA} ${GRUB_CMDLINE_LINUX_DEFAULT}" \
      quiet
```

---

### Post by CharlesA on 2010-03-17
Yeah, you should remove "false"

It should looks like this:

```
  linux_entry "${OS} ${version_no_generic}" \
```

The problem I had was if I updated the variable with the name I wanted, it would leave off "recovery mode" so I did a quick and dirty workaround:

I had to edit /boot/grub/menu.lst on the BT4 install and then running "update-grub" from Ubuntu 9.10.

Original menu.lst:

```
title		Ubuntu 8.10, kernel 2.6.30.9
uuid		a76c7835-eb6f-459f-a891-496f16bc00eb
kernel		/boot/vmlinuz-2.6.30.9 root=UUID=a76c7835-eb6f-459f-a891-496f16bc00eb ro vga=0x317 
initrd		/boot/initrd.img-2.6.30.9
quiet

title		Ubuntu 8.10, kernel 2.6.30.9 (recovery mode)
uuid		a76c7835-eb6f-459f-a891-496f16bc00eb
kernel		/boot/vmlinuz-2.6.30.9 root=UUID=a76c7835-eb6f-459f-a891-496f16bc00eb ro  single
initrd		/boot/initrd.img-2.6.30.9

title		Ubuntu 8.10, memtest86+
uuid		a76c7835-eb6f-459f-a891-496f16bc00eb
kernel		/boot/memtest86+.bin
quiet

```

Edited menu.lst:

```
title		**Backtrack 4 Final (2.6.30.9)**
uuid		8ce79a61-7653-4799-950e-bca17e0b5b77
kernel		/boot/vmlinuz-2.6.30.9 root=UUID=8ce79a61-7653-4799-950e-bca17e0b5b77 ro quiet splash 
initrd		/boot/initrd.img-2.6.30.9
quiet

title		**Backtrack 4 Final (.6.30.92)** (recovery mode)
uuid		8ce79a61-7653-4799-950e-bca17e0b5b77
kernel		/boot/vmlinuz-2.6.30.9 root=UUID=8ce79a61-7653-4799-950e-bca17e0b5b77 ro  single
initrd		/boot/initrd.img-2.6.30.9

#title		Ubuntu 8.10, memtest86+
#uuid		8ce79a61-7653-4799-950e-bca17e0b5b77
kernel		/boot/memtest86+.bin
quiet

```

Here is what my Grub2 menu looks like now:

```
Karmic (2.6.31-20)
Karmic (2.6.31-20) (recovery mode)
Karmic (2.6.31-14)
Karmic (2.6.31-14) (recovery mode)
Windows 7 Professional
Backtrack 4 Final (2.6.30.9)
Backtrack 4 Final (2.6.30.9) (recovery mode)
```

Much, much cleaner.

---

### Post by dr_psikick on 2010-04-04
I used to have in the previous Grub version an entry for booting USB devices (portable OS's).

Can I do one entry like that in GRUB2?
If so, does anyone know where and how sould I add it?

Thanks

---

### Post by dr_psikick on 2010-04-04
I used to have in the previous Grub version an entry for booting USB devices (portable OS's).

Can I do one entry like that in GRUB2?
If so, does anyone know where and how sould I add it?

Thanks

---

### Post by drs305 on 2010-04-04
> **dr_psikick said:**
> I used to have in the previous Grub version an entry for booting USB devices (portable OS's).

Can I do one entry like that in GRUB2?
If so, does anyone know where and how sould I add it?

Thanks

Probably the best place to add it would be to a custom menu. There is already a blank /etc/grub.d/40_custom file to which you could add the entry. This will place the entry at the bottom of the list. If you want it at the top, rename the file (or create a new one called) 06_custom  (the number determines the location).

As to what the contents of the menuentry would be, if you post your old Grub legacy entry someone should be able to help 'translate' it into Grub2.

---

### Post by dr_psikick on 2010-04-05
> **drs305 said:**
> Probably the best place to add it would be to a custom menu. There is already a blank /etc/grub.d/40_custom file to which you could add the entry. This will place the entry at the bottom of the list. If you want it at the top, rename the file (or create a new one called) 06_custom  (the number determines the location).

As to what the contents of the menuentry would be, if you post your old Grub legacy entry someone should be able to help 'translate' it into Grub2.

Thanks for the input, I really don't care about the location on the grub menu, so at the end would be just fine.

In the previous version my USB entry looked like this:

root: (hd1,0)
make active: yes
chainloader: +1


so if someone can help me in creating one entry for GRUB2 for booting USB devices I would be really thankful.

---

### Post by k3lt01 on 2010-04-07
Great thread but I'm having a little difficulty with the title of the Recovery mode.

> **drs305 said:**
> 
[SIZE=3]**[COLOR=DarkRed]1. /etc/grub.d/10_linux[/COLOR]**[/SIZE] - [SIZE=3]**[COLOR=Navy]Changing/Limiting Ubuntu/Linux Titles[/COLOR]**[COLOR=Navy] (on default partition)[/COLOR][/SIZE]

[LIST]
[*][SIZE=3]**A. Changing Linux Titles on Main Partition**[/SIZE]

```
gksu gedit /etc/grub.d/10_linux
```
[LIST]
[*]Defined Variable Examples:  **${OS}** *Ubuntu, Kubuntu*, etc.; **${version}** *2.6.31-11, 2.6.31-11-generic*, etc.
Added Variable Example:  **${codename}** *karmic*
[*]Add new variables ***[COLOR=Navy]codename[/COLOR]*** and ***[COLOR=Navy]version_no_generic[/COLOR]***. The list of variables in 10_linux begins at approximately line 87.
[LIST]
[*]**If *Recovery* modes are displayed, make the change in that section as well. It's the next section of 10_linux.**

Below is my 10_linux file and while I have Karmic showing correctly in GRUB I am having difficulty with getting the recovery mode to show the Karmic title instead of the standard recovery title.

```
#! /bin/sh -e

# grub-mkconfig helper script.
# Copyright (C) 2006,2007,2008,2009  Free Software Foundation, Inc.
#
# GRUB is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# GRUB is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with GRUB.  If not, see <http://www.gnu.org/licenses/>.

prefix=/usr
exec_prefix=${prefix}
libdir=${exec_prefix}/lib
. ${libdir}/grub/grub-mkconfig_lib

if [ "x${GRUB_DISTRIBUTOR}" = "x" ] ; then
  OS=GNU/Linux
else
  OS="${GRUB_DISTRIBUTOR}"
fi

# loop-AES arranges things so that /dev/loop/X can be our root device, but
# the initrds that Linux uses don't like that.
case ${GRUB_DEVICE} in
  /dev/loop/*|/dev/loop[0-9])
    GRUB_DEVICE=`losetup ${GRUB_DEVICE} | sed -e "s/^[^(]*(\([^)]\+\)).*/\1/"`
    # We can't cope with devices loop-mounted from files here.
    case ${GRUB_DEVICE} in
      /dev/*) ;;
      *) exit 0 ;;
    esac
  ;;
esac

if [ "x${GRUB_DEVICE_UUID}" = "x" ] || [ "x${GRUB_DISABLE_LINUX_UUID}" = "xtrue" ] \
    || ! test -e "/dev/disk/by-uuid/${GRUB_DEVICE_UUID}" \
    || [ "`grub-probe -t abstraction --device ${GRUB_DEVICE} | sed -e 's,.*\(lvm\).*,\1,'`" = "lvm"  ] ; then
  LINUX_ROOT_DEVICE=${GRUB_DEVICE}
else
  LINUX_ROOT_DEVICE=UUID=${GRUB_DEVICE_UUID}
fi

# add crashkernel option if we have the required tools
if [ -x "/usr/bin/makedumpfile" ] && [ -x "/sbin/kexec" ]; then
    GRUB_CMDLINE_EXTRA="$GRUB_CMDLINE_EXTRA crashkernel=384M-2G:64M,2G-:128M"
fi

linux_entry ()
{
  cat << EOF
menuentry "$1" {
        recordfail=1
        if [ -n \${have_grubenv} ]; then save_env recordfail; fi
EOF
  if [ "x$3" = "xquiet" ]; then
    cat << EOF
	set quiet=1
EOF
  fi
  save_default_entry | sed -e "s/^/\t/"
  prepare_grub_to_access_device ${GRUB_DEVICE_BOOT} | sed -e "s/^/\t/"
  cat << EOF
	linux	${rel_dirname}/${basename} root=${linux_root_device_thisversion} ro $2
EOF
  if test -n "${initrd}" ; then
    cat << EOF
	initrd	${rel_dirname}/${initrd}
EOF
  fi
  cat << EOF
}
EOF
}

list=`for i in /boot/vmlinu[xz]-* /vmlinu[xz]-* ; do
        if grub_file_is_not_garbage "$i" ; then echo -n "$i " ; fi
      done`

while [ "x$list" != "x" ] ; do
  linux=`version_find_latest $list`
  echo "Found linux image: $linux" >&2
  basename=`basename $linux`
  dirname=`dirname $linux`
  rel_dirname=`make_system_path_relative_to_its_root $dirname`
  version=`echo $basename | sed -e "s,^[^0-9]*-,,g"`
  alt_version=`echo $version | sed -e "s,\.old$,,g"`
  linux_root_device_thisversion="${LINUX_ROOT_DEVICE}"
# User-added variable
  codename="`lsb_release -cs`"
  Codename="`echo $codename | tr [hjkl] [HJKL]`"
  version_no_generic="`echo ${version} | cut -d "-" -f 1-2`"

  initrd=
  for i in "initrd.img-${version}" "initrd-${version}.img" \
	   "initrd-${version}" "initrd.img-${alt_version}" \
	   "initrd-${alt_version}.img" "initrd-${alt_version}"; do
    if test -e "${dirname}/${i}" ; then
      initrd="$i"
      break
    fi
  done
  if test -n "${initrd}" ; then
    echo "Found initrd image: ${dirname}/${initrd}" >&2
  else
    # "UUID=" magic is parsed by initrds.  Since there's no initrd, it can't work here.
    linux_root_device_thisversion=${GRUB_DEVICE}
  fi

  linux_entry "${codename} ${version}" \
      "${GRUB_CMDLINE_LINUX} ${GRUB_CMDLINE_EXTRA} ${GRUB_CMDLINE_LINUX_DEFAULT}" \
      quiet
  if [ "x${GRUB_DISABLE_LINUX_RECOVERY}" != "xtrue" ]; then
    linux_entry "${OS}, Linux ${version} (recovery mode)" \
	"single ${GRUB_CMDLINE_LINUX}"
  fi

  list=`echo $list | tr ' ' '\n' | grep -vx $linux | tr '\n' ' '`
done
```Where about would I put the modification within the Recovery section? I have tried a few places but nothing is working for me.

---

### Post by drs305 on 2010-04-07
> **k3lt01 said:**
> Great thread but I'm having a little difficulty with the title of the Recovery mode.


```

# User-added variable
  codename="`lsb_release -cs`"
  Codename="`echo $codename | tr [hjkl] [HJKL]`"
  version_no_generic="`echo ${version} | cut -d "-" -f 1-2`"

  initrd=
  for i in "initrd.img-${version}" "initrd-${version}.img" \
	   "initrd-${version}" "initrd.img-${alt_version}" \
	   "initrd-${alt_version}.img" "initrd-${alt_version}"; do
    if test -e "${dirname}/${i}" ; then
      initrd="$i"
      break
    fi
  done
  if test -n "${initrd}" ; then
    echo "Found initrd image: ${dirname}/${initrd}" >&2
  else
    # "UUID=" magic is parsed by initrds.  Since there's no initrd, it can't work here.
    linux_root_device_thisversion=${GRUB_DEVICE}
  fi

  linux_entry "${codename} ${version}" \
      "${GRUB_CMDLINE_LINUX} ${GRUB_CMDLINE_EXTRA} ${GRUB_CMDLINE_LINUX_DEFAULT}" \
      quiet
  if [ "x${GRUB_DISABLE_LINUX_RECOVERY}" != "xtrue" ]; then
    [COLOR="DarkRed"]**linux_entry "${OS}, Linux ${version} (recovery mode)" \**[/COLOR]
	"single ${GRUB_CMDLINE_LINUX}"
  fi


```

Where about would I put the modification within the Recovery section? I have tried a few places but nothing is working for me.

For me, testing lucid, to get a menu item "lucid 2.6.32-19-generic (recovery mode)" 
change the bold dark red section above to:
> 
    **[COLOR="DarkRed"]linux_entry "${codename} ${version} (recovery mode)"[/COLOR]** \


I think that is what you are looking for. Don't forget to update-grub after saving the change.

---

### Post by k3lt01 on 2010-04-07
> **drs305 said:**
> Don't forget to update-grub after saving the change.Nothing has changed I keep getting this after I update GRUB
```
michael@michael-laptop:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
/etc/grub.d/10_linux: 126: single : not found
```I'm assuming 126: is line 126 which is the new last line after I did the first modification a couple of weeks back. When I reboot I still have the normal non title recovery selection while the non recovery says Karmic.

I'll keep playing around with it, and I'll give it a go on Lucid later to see if that behaves differently.

---

### Post by drs305 on 2010-04-08
k3lt01,

> /etc/grub.d/10_linux: 126: single : not found

This just means there is an error somewhere in script. Line 126 is the last line in your file. The script is telling you that it went all the way to the end of the file and there were still issues yet unresolved. In this case, it involves the line with "single" in it. 

It could be something as simple as an extra space at the end of the line, the way the quotation symbols are interpreted in your text editor, etc. Also make sure you don't have an old script (for instance 10_linux.bad) in the /etc/grub.d folder that is still executable. Any executable file in the folder may run when update-grub is invoked.

I don't have the time right now to go through the script and troubleshoot it, although running it on my computer currently produces no errors. I'll try to explore it more completely as soon as I have a bit of free time.

**[COLOR="DarkRed"]Added:[/COLOR]** I was able to generate the same error message you received by placing a space at the end of the line prior to the line containing "single".

---

### Post by k3lt01 on 2010-04-08
> **drs305 said:**
>  In this case, it involves the line with "single" in it. 

It could be something as simple as an extra space at the end of the line, Fixed it, it was the line above "single"
```
linux_entry "${codename} ${version} (recovery mode)" \
```
The issue was something to do with spacing it made no difference where the line started in the original file but in the modified file that line had two spaces to many at the start.

Thanks again for your help.

---

### Post by Larkster on 2010-04-18
> **drs305 said:**
> 

[LIST]
[*]
[LIST]
[*] [SIZE=3]**Original Menu Entry: [COLOR=DarkRed]Windows XP Home *(on /dev/sda7)*[/COLOR]**[/SIZE] 
Approximately line 150.
```

menuentry "${LONGNAME} **[COLOR=Red](on ${DEVICE})[/COLOR]**" {

```[SIZE=3]**New Format: [COLOR=DarkRed]Windows XP Home [/COLOR] [COLOR=DarkGreen](sda1)[/COLOR]**[/SIZE] 
```

menuentry "${LONGNAME}"**[COLOR=Navy] (${shortdevice}) {[/COLOR]**

```
[/LIST]
 
[/LIST]
 Perhaps I'm wrong, but it appears that the end quote comes too soon (before the (${shortdevice}) part of the name). Thus, it should look like:
```

menuentry "${LONGNAME} (${shortdevice})**[COLOR=Red]"[/COLOR]** {

```This typo appears again in the subsequent title tweak as well...

---

### Post by drs305 on 2010-04-18
Larkster,

Thank you for pointing this out. Corrected in the original post.

And welcome to the Ubuntu forums.  :-)

---

### Post by Larkster on 2010-04-18
Thank you for such a great post. I'm glad there are other people out there that are anal about the appearance of their Grub menu too. At first I was very cautious about modifying it, for fear of messing something up, but now I feel like I've learned so much from going through this tweaking process. Thanks!

---

### Post by kchealee on 2010-04-25
Great tutorial and so easy to understand i like it ! =D>
Anyway I found this trick will **[COLOR=Red]remove a menu entry or even a linux recovery[/COLOR]** while i playing around with it. :) hope it work and not double post.

just assign value '--' to LONGNAME (LONGNAME = "--") or linux_entry (linux_entry "--")

Remove a windows menu entry
```

if [ "${LONGNAME}" = "menu title here" ] ; then
  LONGNAME= "--"
elif [ -z "${LONGNAME}" ] ; then
  LONGNAME="${LABEL}"
fi

```Remove a linux recovery mode
```

# ORIGINAL linux_entry "${OS}, Linux ${version} (recovery mode)" \
linux_entry "--" \

```

---

### Post by ankit.vader on 2010-04-26
hi.....I have Lenovo Y500 series laptop and I found that when ever I boot system , my keyboard worked  some times and some times not .Same thing was happening with my touchpad.

After some googling I found out that it’s neither a problem of Operating System  nor a misconfiguration of X11 config file.

It is a problem related to acpi and the 8042 interrupt controller conflicts.

So to get rid of this problem is to edit your  grub configuration file ./boot/grub/menu.lst ( on ubuntu)  and append  the following  line to the  kernel argument.

locale=fr_FR i8042.reset
but with grub2 i dont understand where to append the following line....```
default=0
timeout=5
splashimage=(hd0,5)/grub/splash.xpm.gz
hiddenmenu
title CentOS (2.6.18-164.11.1.el5)
root (hd0,5)
kernel /vmlinuz-2.6.18-164.11.1.el5 ro root=/dev/VolGroup00/LogVol00 rhgb quiet splash
initrd /initrd-2.6.18-164.11.1.el5.imga
```
I have highlighted the line the be changed. Append the ‘locale=fr_FR i8042.reset’ to the following line.Depending on your grub file, you have to find line having kernel and modify it. After the changes, file is.
```
default=0
timeout=5
splashimage=(hd0,5)/grub/splash.xpm.gz
hiddenmenu
title CentOS (2.6.18-164.11.1.el5)
root (hd0,5)
kernel /vmlinuz-2.6.18-164.11.1.el5 ro root=/dev/VolGroup00/LogVol00 rhgb quiet splash locale=fr_FR i8042.reset 
initrd /initrd-2.6.18-164.11.1.el5.imga
```

need help...

---

### Post by dr_psikick on 2010-04-27
> **dr_psikick said:**
> Thanks for the input, I really don't care about the location on the grub menu, so at the end would be just fine.

In the previous version my USB entry looked like this:

root: (hd1,0)
make active: yes
chainloader: +1


so if someone can help me in creating one entry for GRUB2 for booting USB devices I would be really thankful.


/bump

Someone? Thanks.

---

### Post by weissnich on 2010-05-06
I have followed 
7. HIDING THE MENU ON MULTI-OS SYSTEMS

and it works after updating grub,
but the file /etc/default/grub is not recognized,
I can't come into the menu with Shift-Key
I want to have 4 seconds hidden timeout with countdown displayed and be able to access the menu with Shift, but it does not show, my lines are:

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=4
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_TIMEOUT=4

Anybody help?

---

### Post by Skara Brae on 2010-05-21
My menu says "Windows Vista", while it should / I want it to be "Windows XP Home". I read the first posting, and it is (probably) me, but the explanation of how to change lines in the GRUB2 menu is incomprehensible to me :(

I tried comparing the content & lines of my "30_os-prober" with the text in the first posting, and I can not find any (enough) comparison :(
I even used the "search" command (you know: CTRL-F) to find correct similarities.

I will just leave it as "Windows Vista"... (until I find an explanation for "n00bs" that I can understand, although I thought I was past the "n00b" stadium).
I am kind of a perfectionist ("XP" is not "Vista"), but then again I guess it doesn't matter *that* much (seeing "Vista" instead of "XP").

-oo-

Editing the GRUB menu of my previous 7.10 install was much easier than GRUB 2. It should be made (much) easier for people like me. This new way of editing the GRUB menu is not good (for much harder). This is just my opinion. Sorry.

---

### Post by Agent.Logic_ on 2010-05-22
Skara Brae,

In section 3.A.1., you are asked to run the command:

```
sudo cat /boot/grub/grub.cfg | grep "menuentry" | cut -d '"' -f 2
```

This will print out all the "menu entries" that you see in GRUB during boot. In my case, this prints out:

```
menuentry 'Ubuntu, with Linux 2.6.32-22-generic --class ubuntu --class gnu-linux.....
....
....
....
menuentry '**Windows Vista (loader) (on /dev/sda1)**
```

If I wanted my Windows entry to say "Windoze Blista", I'd copy the title **Windows Vista (loader) (on /dev/sda1)**, paste it like it is directed in section 3.A.4. (highlighted in red), and enter "Windoze Blista" in the next line (highlighted in blue). This **if [ -z ${LONGNAME}...** code appears in line 140 of the 30_os-prober file.

You might also want to look into the "[Custom Menu]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu")" option in GRUB2. I agree with you that GRUB2 title tweaking is a bit hard to get head or tail of at first, you need a little patience trying to understand all of it. It took me a while to get a hang of it, but I like the "Custom Menu" option better because:

a) I can have titles like "Windoze Blista" or whatever I want it to be
b) It is relatively simpler (atleast it seems that way) than "regular" title tweaking.

It does come with its downsides though... Although you'd never have to edit the custom menu again for every time there is a kernel upgrade, if you are used to having the two most recent kernels in your boot menu, you'd have to edit the 2nd most recent kernel every time you upgrade.

Hope this helps (and hope I made sense!).

---

### Post by Skara Brae on 2010-05-24
Agent.Logic_

First of all - thank you very much for having taken the time to respond.

I took the time to re-read the explanation about GRUB2 again, and I _thought_ I had done it correctly just a minute ago, but after restarting my PC, it still says "Windows Vista" (or whatever it precisely says).

With GRUB I would have changed it long ago; I have done it in the past more than once, with 7.10 and also with Xubuntu 8.04. It was much easier (just perfect for a n00b with a bit of "under the hood" experience in Linux like myself).

I probably do something wrong (duh!), but I am not sure what exactly. I'll look into it again some other time...

-oo-

Whatever the reason may be to change something, making it more "complicated" than it was before is not a good change, in my opinion.

---

### Post by drs305 on 2010-05-24
Skara Brae,

Added: I think the problem may be that the title would not be "Windows Vista (loader) (on /dev/sda1)" but would be "Windows Vista (loader)" or possibly "Windows Vista". The "(on /dev/sda1)" is the result of the ${DEVICE} portion of the script. If you are trying to match the ${LONGNAME}, don't include the "on /dev/sda1".  If that doesn't fix things, then:

If you post your 30_os-prober file I'll be happy to take a look at it. Just put it between "code" tags by clicking on the # icon in the post's menu.

---

### Post by Agent.Logic_ on 2010-05-26
I agree with drs305. It could be a DEVICE/LONGNAME issue. Why don't you post the entire contents of 30_os-prober file like he suggested, then we can see what's causing it to stay "Windows Vista."

> Whatever the reason may be to change something, making it more "complicated" than it was before is not a good change, in my opinion.

Well, GRUB is undergoing a sea of change. They wouldn't make it more "complicated" on purpose unless they had a reason to: making it more powerful, advanced and robust. I know it's frustrating having to get used the apparently kazillion new options available now, but it's all for the good.

---

### Post by Darktrax on 2010-05-30
> **Agent.Logic_ said:**
>  I know it's frustrating having to get used the apparently kazillion new options available now, but it's all for the good.

Does anyone still think that, for the average user, having to edit executable scripts just to get the impenetrable (but updateable)  'titles' re-worked into something meaningful is easier, less risky, friendlier, more intuitive, robust????

I have read this thread through. It contains accurate and excellent advice. You need to be doing ***root authorized*** operations. You need to ***back up*** the scripts you mess with from /etc/grub.d. You need to watch out for your ***speling mistaikes***. You need to be ***certain*** to an extraordinary degree that you got it right!

This is because there comes a point where you have to shut down for re-boot, and then discover that you hosed the route back in to successfully re-booting your machine. The next step of fixing it via a liveCD intervention to find and fix the fumble is arguably worse than a re-install (for the ***average application user***, that is..).

 The motivations behind this are clear. The first arrangements to add executeable update stuff to *menu.lst* in such a way that grub would still only see additions as comments gave us those wonderful double ## and triple ### hash signs from Debian. (It would seem they are still with us in grub2)  Now we have executable files that write other executable files!

Don't get me wrong folks - I am all agreed that the experts have done great work to make a new system with all kinds of benefits, even if mostly useful to other experts. I just think they lost sight of the needs of the ultimate user. I need a ***low risk*** tool to make an initial menu I want, maybe with ways to make it open further to display memory testing and recover options. For now, I have to settle for a little *Post-It* note that decodes which option is actually Ubuntu-Studio, PureDyne, etc.  among other OS kernels.

---

### Post by drs305 on 2010-05-30
Darktrax,

I agree with much of what you say. The solution IMO is for someone to develop a nice GUI tool (StartUp-Manager 2?) which can perform most of these tasks. 

The scripts are fairly straightforward and it would not be extremely complicated to create a small app which could do most of the tweaks herein: set the timeout, default OS, choose the wallpaper, rename or hide titles, change the menu resolution, etc. StartUp-Manager can do some of them but not all.

Of course, it's easy to volunteer other people's time, but the GUI users of Linux/Ubuntu would be extremely grateful for such an app and someday one will probably appear.

---

### Post by Darktrax on 2010-05-31
> **drs305 said:**
>  The solution IMO is for someone to develop a nice GUI tool (StartUp-Manager 2?) which can perform most of these tasks. 
drs305,  

I am sure there are lots of things our folk would suggest in the wish list list for a **grub GUI "first appearance view and features"** discussion.

For me, having to tell a retired lady just getting used to the joys of internet access with a new laptop, featuring Lucid worked up to be somewhat prettier than the default, to just touch nothing until the grub display went away by itself.. was a little disappointing!

I do agree that the folk who did all this work (for others who were volunteering their time!), do not deserve piles of negative critique. They wrote it, so they have some right to say how it works. Even so, I would offer the suggestion that **UN-commenting** lines to **DIS-able** features (double-negative!) is not the way to make it easier, and surely not too awkward to turn the logic around. I much prefer that to comment a line out means the feature is not there. Leave the line in - and it does what it says. For something as important as whether the PC will boot again, at my level of meddle-ability, I do not want to be editing these scripts!

---

### Post by k3lt01 on 2010-06-01
> **Darktrax said:**
> For me, having to tell a retired lady just getting used to the joys of internet access with a new laptop, featuring Lucid worked up to be somewhat prettier than the default, to just touch nothing until the grub display went away by itself.. was a little disappointing!This begs the question of: Why is GRUB being displayed anyway on a machine that probably only has one OS on it? Or am I missing something here?

---

### Post by n1ght5t4lk3r on 2010-06-01
Great thread, it sorted out a little quandry of mine from another thread. Thanks _**drs305**_ for directing me here.

and for this guys issue...

> **drs305 said:**
> Skara Brae,

Added: I think the problem may be that the title would not be "Windows Vista (loader) (on /dev/sda1)" but would be "Windows Vista (loader)" or possibly "Windows Vista". The "(on /dev/sda1)" is the result of the ${DEVICE} portion of the script. If you are trying to match the ${LONGNAME}, don't include the "on /dev/sda1".  If that doesn't fix things, then:

If you post your 30_os-prober file I'll be happy to take a look at it. Just put it between "code" tags by clicking on the # icon in the post's menu.

I can say that its almost likely the issue, since I followed the directions and to start ended up with no change in the name I desired to change, but then after the above quoted reply I dropped the "(on /dev/sda1)" or in my case sda2, and it worked perfectly.

---

### Post by drs305 on 2010-06-01
> **n1ght5t4lk3r said:**
> I can say that its almost likely the issue, since I followed the directions and to start ended up with no change in the name I desired to change, but then after the above quoted reply I dropped the "(on /dev/sda1)" or in my case sda2, and it worked perfectly.

Since at least 2 users experienced the same problem I've gone back to the original post and emphasized that the title does not include the "on /dev/sdXX" portion. 

Thanks for the feedback!

---

### Post by Darktrax on 2010-06-02
> **k3lt01 said:**
> This begs the question of: Why is GRUB being displayed anyway on a machine that probably only has one OS on it? Or am I missing something here?

The laptop also had Jaunty on it, as a slightly desperate solution to getting it to fix itself up onto the available network, using a disk we had handy. Then we tried 10.04 Lucid again. It was not a good day  :(

---

### Post by Skara Brae on 2010-06-08
First - my apologies for not having replied sooner; I have more than one (or two) computer(s), and I try to use them all regulary, which means I don't use this PC, with Ubuntu, every day/time.

-oo-

Whatever I try, I don't seem to get "*Windows Vista (loader) (on /dev/sda1)*" changed into "*Windows XP Home*" :confused:

Here is my original 30_os-prober file
(Do you really need the entire file? All 260 lines?
It's Chinese to me (I see GNU/Linux is not for the average Windows user :p  I mean, just look how much "trouble" a n00b like me has with changing one, small, single word ("Vista")...)

```

#! /bin/sh -e

# grub-mkconfig helper script.
# Copyright (C) 2006,2007,2008,2009  Free Software Foundation, Inc.
#
# GRUB is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# GRUB is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with GRUB.  If not, see <http://www.gnu.org/licenses/>.

prefix=/usr
exec_prefix=${prefix}
libdir=${exec_prefix}/lib

. ${libdir}/grub/grub-mkconfig_lib

found_other_os=

adjust_timeout () {
  if [ "x${found_other_os}" = "x" ] ; then
    if [ "x${GRUB_HIDDEN_TIMEOUT}" != "x" ] ; then
      if [ "x${GRUB_HIDDEN_TIMEOUT_QUIET}" = "xtrue" ] ; then
	verbose=
      else
	verbose=" --verbose"
      fi

      if [ "x${GRUB_HIDDEN_TIMEOUT}" = "x0" ] ; then
	cat <<EOF
if [ \${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep$verbose --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
EOF
      else
	cat << EOF
if [ \${timeout} != -1 ]; then
  if sleep$verbose --interruptible ${GRUB_HIDDEN_TIMEOUT} ; then
    set timeout=0
  fi
fi
EOF
      fi
    fi
  fi
}

if [ "x${GRUB_DISABLE_OS_PROBER}" = "xtrue" ]; then
  adjust_timeout
  exit 0
fi

if [ -z "`which os-prober 2> /dev/null`" -o -z "`which linux-boot-prober 2> /dev/null`" ] ; then
  # missing os-prober and/or linux-boot-prober
  adjust_timeout
  exit 0
fi

OSPROBED="`os-prober | tr ' ' '^' | paste -s -d ' '`"
if [ -z "${OSPROBED}" ] ; then
  # empty os-prober output, nothing doing
  adjust_timeout
  exit 0
fi

osx_entry() {
        cat << EOF
menuentry "${LONGNAME} (${2}-bit) (on ${DEVICE})" {
EOF
	save_default_entry | sed -e "s/^/\t/"
	prepare_grub_to_access_device ${DEVICE} | sed -e "s/^/\t/"
	cat << EOF
        insmod ${GRUB_VIDEO_BACKEND}
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ \$do_resume == 0 ]; then
           xnu_uuid ${OSXUUID} uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           $1 /mach_kernel boot-uuid=\${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
EOF
}

for OS in ${OSPROBED} ; do
  DEVICE="`echo ${OS} | cut -d ':' -f 1`"
  LONGNAME="`echo ${OS} | cut -d ':' -f 2 | tr '^' ' '`"
  LABEL="`echo ${OS} | cut -d ':' -f 3 | tr '^' ' '`"
  BOOT="`echo ${OS} | cut -d ':' -f 4`"

  if [ -z "${LONGNAME}" ] ; then
    LONGNAME="${LABEL}"
  fi

  if [ "${LONGNAME}" = "Windows Vista (loader) (on /dev/sda1)" ] ; then

  echo "Found ${LONGNAME} on ${DEVICE}" >&2
  found_other_os=1

  case ${BOOT} in
    chain)

      cat << EOF
menuentry "${LONGNAME} (on ${DEVICE})" {
EOF
      save_default_entry | sed -e "s/^/\t/"
      prepare_grub_to_access_device ${DEVICE} | sed -e "s/^/\t/"

      case ${LONGNAME} in
	Windows\ Vista*|Windows\ 7*)
	;;
	*)
	  cat << EOF
	drivemap -s (hd0) \${root}
EOF
	;;
      esac

      cat <<EOF
	chainloader +1
}
EOF
    ;;
    linux)
      LINUXPROBED="`linux-boot-prober ${DEVICE} 2> /dev/null | tr ' ' '^' | paste -s -d ' '`"
      prepare_boot_cache=

      for LINUX in ${LINUXPROBED} ; do
        LROOT="`echo ${LINUX} | cut -d ':' -f 1`"
        LBOOT="`echo ${LINUX} | cut -d ':' -f 2`"
        LLABEL="`echo ${LINUX} | cut -d ':' -f 3 | tr '^' ' '`"
        LKERNEL="`echo ${LINUX} | cut -d ':' -f 4`"
        LINITRD="`echo ${LINUX} | cut -d ':' -f 5`"
        LPARAMS="`echo ${LINUX} | cut -d ':' -f 6- | tr '^' ' '`"

        if [ -z "${LLABEL}" ] ; then
          LLABEL="${LONGNAME}"
        fi

	if [ "${LROOT}" != "${LBOOT}" ]; then
	  LKERNEL="${LKERNEL#/boot}"
	  LINITRD="${LINITRD#/boot}"
	fi

        cat << EOF
menuentry "${LLABEL} (on ${DEVICE})" {
EOF
	save_default_entry | sed -e "s/^/\t/"
	if [ -z "${prepare_boot_cache}" ]; then
	  prepare_boot_cache="$(prepare_grub_to_access_device ${LBOOT} | sed -e "s/^/\t/")"
	fi
	printf '%s\n' "${prepare_boot_cache}"
	cat <<  EOF
	linux ${LKERNEL} ${LPARAMS}
EOF
        if [ -n "${LINITRD}" ] ; then
          cat << EOF
	initrd ${LINITRD}
EOF
        fi
        cat << EOF
}
EOF
      done
    ;;
    macosx)
      OSXUUID="`grub-probe --target=fs_uuid --device ${DEVICE} 2> /dev/null`"
      osx_entry xnu_kernel 32
      osx_entry xnu_kernel64 64
    ;;
    hurd)
      cat << EOF
menuentry "${LONGNAME} (on ${DEVICE})" {
EOF
      save_default_entry | sed -e "s/^/\t/"
      prepare_grub_to_access_device ${DEVICE} | sed -e "s/^/\t/"
      grub_device="`${grub_probe} --device ${DEVICE} --target=drive`"
      mach_device="`echo "${grub_device}" | tr -d '()' | tr , s`"
      grub_fs="`${grub_probe} --device ${DEVICE} --target=fs`"
      case "${grub_fs}" in
	*fs)	hurd_fs="${grub_fs}" ;;
	*)	hurd_fs="${grub_fs}fs" ;;
      esac
      cat << EOF
	multiboot /boot/gnumach.gz root=device:${mach_device}
	module /hurd/${hurd_fs}.static ${hurd_fs} --readonly \\
			--multiboot-command-line='\${kernel-command-line}' \\
			--host-priv-port='\${host-port}' \\
			--device-master-port='\${device-port}' \\
			--exec-server-task='\${exec-task}' -T typed '\${root}' \\
			'\$(task-create)' '\$(task-resume)'
	module /lib/ld.so.1 exec /hurd/exec '\$(exec-task=task-create)'
}
EOF
    ;;
    *)
      echo "  ${LONGNAME} is not yet supported by grub-mkconfig." >&2
    ;;
  esac
done

adjust_timeout

```

---

### Post by drs305 on 2010-06-08
> **Skara Brae said:**
> Whatever I try, I don't seem to get "*Windows Vista (loader) (on /dev/sda1)*" changed into "*Windows XP Home*" :confused:
Skara Brae,

Your 30_os-prober is a bit different than the one I am working with. It already has a direct entry for "Windows Vista" which makes it likely this file was modified and not the original. But that's okay. We should be able to make one change to get it to say "XP". The green text is the modified area. The red is the title change.

Make sure you have a copy of your *original* 30_os-prober file (and that it is unexecutable), then copy this file into /etc/grub.d/ to replace it.

```

#! /bin/sh -e

# grub-mkconfig helper script.
# Copyright (C) 2006,2007,2008,2009  Free Software Foundation, Inc.
#
# GRUB is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# GRUB is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with GRUB.  If not, see <http://www.gnu.org/licenses/>.

prefix=/usr
exec_prefix=${prefix}
libdir=${exec_prefix}/lib

. ${libdir}/grub/grub-mkconfig_lib

found_other_os=

adjust_timeout () {
  if [ "x${found_other_os}" = "x" ] ; then
    if [ "x${GRUB_HIDDEN_TIMEOUT}" != "x" ] ; then
      if [ "x${GRUB_HIDDEN_TIMEOUT_QUIET}" = "xtrue" ] ; then
	verbose=
      else
	verbose=" --verbose"
      fi

      if [ "x${GRUB_HIDDEN_TIMEOUT}" = "x0" ] ; then
	cat <<EOF
if [ \${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep$verbose --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
EOF
      else
	cat << EOF
if [ \${timeout} != -1 ]; then
  if sleep$verbose --interruptible ${GRUB_HIDDEN_TIMEOUT} ; then
    set timeout=0
  fi
fi
EOF
      fi
    fi
  fi
}

if [ "x${GRUB_DISABLE_OS_PROBER}" = "xtrue" ]; then
  adjust_timeout
  exit 0
fi

if [ -z "`which os-prober 2> /dev/null`" -o -z "`which linux-boot-prober 2> /dev/null`" ] ; then
  # missing os-prober and/or linux-boot-prober
  adjust_timeout
  exit 0
fi

OSPROBED="`os-prober | tr ' ' '^' | paste -s -d ' '`"
if [ -z "${OSPROBED}" ] ; then
  # empty os-prober output, nothing doing
  adjust_timeout
  exit 0
fi

osx_entry() {
        cat << EOF
menuentry "${LONGNAME} (${2}-bit) (on ${DEVICE})" {
EOF
	save_default_entry | sed -e "s/^/\t/"
	prepare_grub_to_access_device ${DEVICE} | sed -e "s/^/\t/"
	cat << EOF
        insmod ${GRUB_VIDEO_BACKEND}
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ \$do_resume == 0 ]; then
           xnu_uuid ${OSXUUID} uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           $1 /mach_kernel boot-uuid=\${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
EOF
}

for OS in ${OSPROBED} ; do
  DEVICE="`echo ${OS} | cut -d ':' -f 1`"
  LONGNAME="`echo ${OS} | cut -d ':' -f 2 | tr '^' ' '`"
  LABEL="`echo ${OS} | cut -d ':' -f 3 | tr '^' ' '`"
  BOOT="`echo ${OS} | cut -d ':' -f 4`"

  if [ -z "${LONGNAME}" ] ; then
    LONGNAME="${LABEL}"
  fi


[COLOR="Navy"]
[COLOR="Green"]  if [ "${LONGNAME}" = "Windows Vista (loader)" ] ; then
LONGNAME=[/COLOR]"[COLOR="Red"]Windows XP[/COLOR][COLOR="Green"]"
  fi[/COLOR][/COLOR]

  echo "Found ${LONGNAME} on ${DEVICE}" >&2
  found_other_os=1

  case ${BOOT} in
    chain)

      cat << EOF
menuentry "${LONGNAME} (on ${DEVICE})" {
EOF
      save_default_entry | sed -e "s/^/\t/"
      prepare_grub_to_access_device ${DEVICE} | sed -e "s/^/\t/"

      case ${LONGNAME} in
        Windows\ Vista*|Windows\ 7*)
	;;
	*)
	  cat << EOF
	drivemap -s (hd0) \${root}
EOF
	;;
      esac

      cat <<EOF
	chainloader +1
}
EOF

    ;;
    linux)
      LINUXPROBED="`linux-boot-prober ${DEVICE} 2> /dev/null | tr ' ' '^' | paste -s -d ' '`"
      prepare_boot_cache=

      for LINUX in ${LINUXPROBED} ; do
        LROOT="`echo ${LINUX} | cut -d ':' -f 1`"
        LBOOT="`echo ${LINUX} | cut -d ':' -f 2`"
        LLABEL="`echo ${LINUX} | cut -d ':' -f 3 | tr '^' ' '`"
        LKERNEL="`echo ${LINUX} | cut -d ':' -f 4`"
        LINITRD="`echo ${LINUX} | cut -d ':' -f 5`"
        LPARAMS="`echo ${LINUX} | cut -d ':' -f 6- | tr '^' ' '`"

        if [ -z "${LLABEL}" ] ; then
          LLABEL="${LONGNAME}"
        fi

	if [ "${LROOT}" != "${LBOOT}" ]; then
	  LKERNEL="${LKERNEL#/boot}"
	  LINITRD="${LINITRD#/boot}"
	fi

        cat << EOF
menuentry "${LLABEL} (on ${DEVICE})" {
EOF
	save_default_entry | sed -e "s/^/\t/"
	if [ -z "${prepare_boot_cache}" ]; then
	  prepare_boot_cache="$(prepare_grub_to_access_device ${LBOOT} | sed -e "s/^/\t/")"
	fi
	printf '%s\n' "${prepare_boot_cache}"
	cat <<  EOF
	linux ${LKERNEL} ${LPARAMS}
EOF
        if [ -n "${LINITRD}" ] ; then
          cat << EOF
	initrd ${LINITRD}
EOF
        fi
        cat << EOF
}
EOF
      done
    ;;
    macosx)
      OSXUUID="`grub-probe --target=fs_uuid --device ${DEVICE} 2> /dev/null`"
      osx_entry xnu_kernel 32
      osx_entry xnu_kernel64 64
    ;;
    hurd)
      cat << EOF
menuentry "${LONGNAME} (on ${DEVICE})" {
EOF
      save_default_entry | sed -e "s/^/\t/"
      prepare_grub_to_access_device ${DEVICE} | sed -e "s/^/\t/"
      grub_device="`${grub_probe} --device ${DEVICE} --target=drive`"
      mach_device="`echo "${grub_device}" | tr -d '()' | tr , s`"
      grub_fs="`${grub_probe} --device ${DEVICE} --target=fs`"
      case "${grub_fs}" in
	*fs)	hurd_fs="${grub_fs}" ;;
	*)	hurd_fs="${grub_fs}fs" ;;
      esac
      cat << EOF
	multiboot /boot/gnumach.gz root=device:${mach_device}
	module /hurd/${hurd_fs}.static ${hurd_fs} --readonly \\
			--multiboot-command-line='\${kernel-command-line}' \\
			--host-priv-port='\${host-port}' \\
			--device-master-port='\${device-port}' \\
			--exec-server-task='\${exec-task}' -T typed '\${root}' \\
			'\$(task-create)' '\$(task-resume)'
	module /lib/ld.so.1 exec /hurd/exec '\$(exec-task=task-create)'
}
EOF
    ;;
    *)
      echo "  ${LONGNAME} is not yet supported by grub-mkconfig." >&2
    ;;
  esac
done

adjust_timeout

```

Run "sudo update-grub" and hopefully you will see "Windows XP" as it finds your 'other' OS.

---

### Post by nyihtut100 on 2010-06-16
i did grub timeout = 0

then i can not see my ubuntu boot loader

machine is directly boot to windows

how can i change it back grub timeout = 2

please help me 

thanks
Nyi

---

### Post by Skara Brae on 2010-06-17
**Skara Brae reporting back in...**

**Yes!**

drs305, I copied the coloured text in 'your' 30_os-prober into mine: now it says "Windows XP Home" instead of Windows Vista (I added the "Home").

I only added those few lines (and commented out another part) and that's it? Why couldn't I do that myself??
Well, don't we feel foolish... :)

> **drs305 said:**
> Skara Brae,

Your 30_os-prober is a bit different than the one I am working with. It already has a direct entry for "Windows Vista" which makes it likely this file was modified and not the original.
I did not change anything in my original 30_os-prober (I didn't even know about the new GRUB version), so it was the original. If I had changed it, then I would have mentioned that, of course: no use messing something up and then asking for help on a forum, while not telling that I would have messed up.

In any case, now the GRUB menu on my machine looks the way it should be. XP is not Vista, and I kind of am a perfectionist :)

**drs305**,
I thank you very much.

-oo-

I still have Windows, because there are a few Windows-only programs that I really don't want to be without (like "PhotoPAINT" from COREL; The GIMP is _no_ alternative, I'd rather work with MS Paint than with The GIMP, no offense). Those few programs are the only reason why I still have "Wintendo" (as a guy from IT at work calls it).

Microsoft Windows is the most unreliable thing I have ever worked with in my entire life. I "hate" it. What a difference (both) GNU/Linux and OS X are.

---

### Post by COKEDUDE on 2010-06-18
Very nice guide. Thx for writing this.

---

### Post by Elfy on 2010-06-18
> **nyihtut100 said:**
> i did grub timeout = 0

then i can not see my ubuntu boot loader

machine is directly boot to windows

how can i change it back grub timeout = 2

please help me 

thanks
Nyi

Press shift while grub loads so you see the menu again - choose ubuntu - ```
gksudo gedit /etc/default/grub
```

Do the changes - save and close then run 

```
sudo update-grub
```

[https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202](https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202)

---

### Post by ssaint04 on 2010-06-20
Well, I seem to have hit a snag. I want my GRUB2 menu to have two entries: One that says simply "Ubuntu" and one that says "Windows 7"

I've got the one that says "Windows 7" down pat.


But the one that should say "Ubuntu" says "Ubuntu, with Linux false"

Can anyone help me figure it out? :confused:

Currently, my 10_linux script looks like this:

```

#! /bin/sh -e

# grub-mkconfig helper script.
# Copyright (C) 2006,2007,2008,2009,2010  Free Software Foundation, Inc.
#
# GRUB is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# GRUB is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with GRUB.  If not, see <http://www.gnu.org/licenses/>.

prefix=/usr
exec_prefix=${prefix}
bindir=${exec_prefix}/bin
libdir=${exec_prefix}/lib
. ${libdir}/grub/grub-mkconfig_lib

export TEXTDOMAIN=grub
export TEXTDOMAINDIR=@LOCALEDIR@

CLASS="--class gnu-linux --class gnu --class os"

if [ "x${GRUB_DISTRIBUTOR}" = "x" ] ; then
  OS=GNU/Linux
else
  OS="${GRUB_DISTRIBUTOR}"
  CLASS="--class $(echo ${GRUB_DISTRIBUTOR} | tr '[A-Z]' '[a-z]' | cut -d' ' -f1) ${CLASS}"
fi

# loop-AES arranges things so that /dev/loop/X can be our root device, but
# the initrds that Linux uses don't like that.
case ${GRUB_DEVICE} in
  /dev/loop/*|/dev/loop[0-9])
    GRUB_DEVICE=`losetup ${GRUB_DEVICE} | sed -e "s/^[^(]*(\([^)]\+\)).*/\1/"`
    # We can't cope with devices loop-mounted from files here.
    case ${GRUB_DEVICE} in
      /dev/*) ;;
      *) exit 0 ;;
    esac
  ;;
esac

if [ "x${GRUB_DEVICE_UUID}" = "x" ] || [ "x${GRUB_DISABLE_LINUX_UUID}" = "xtrue" ] \
    || ! test -e "/dev/disk/by-uuid/${GRUB_DEVICE_UUID}" \
    || [ "`grub-probe -t abstraction --device ${GRUB_DEVICE} | sed -e 's,.*\(lvm\).*,\1,'`" = "lvm"  ] ; then
  LINUX_ROOT_DEVICE=${GRUB_DEVICE}
else
  LINUX_ROOT_DEVICE=UUID=${GRUB_DEVICE_UUID}
fi

# add crashkernel option if we have the required tools
if [ -x "/usr/bin/makedumpfile" ] && [ -x "/sbin/kexec" ]; then
    GRUB_CMDLINE_EXTRA="$GRUB_CMDLINE_EXTRA crashkernel=384M-2G:64M,2G-:128M"
fi

linux_entry ()
{
  os="$1"
  version="$2"
  recovery="$3"
  args="$4"
  if ${recovery} ; then
    title="$(gettext_quoted "%s, with Linux %s (recovery mode)")"
  else
    title="$(gettext_quoted "%s, with Linux %s")"
  fi
  printf "menuentry '${title}' ${CLASS} {\n" "${os}" "${version}"
  cat << EOF
	recordfail
EOF
  save_default_entry | sed -e "s/^/\t/"

  if [ "x$GRUB_GFXPAYLOAD_LINUX" != x ]; then
	  cat << EOF
	set gfxpayload=$GRUB_GFXPAYLOAD_LINUX
EOF
  fi

  if [ -z "${prepare_boot_cache}" ]; then
    prepare_boot_cache="$(prepare_grub_to_access_device ${GRUB_DEVICE_BOOT} | sed -e "s/^/\t/")"
  fi
  printf '%s\n' "${prepare_boot_cache}"
  if [ "x$5" != "xquiet" ]; then
    cat << EOF
	echo	'$(printf "$(gettext_quoted "Loading Linux %s ...")" ${version})'
EOF
  fi
  cat << EOF
	linux	${rel_dirname}/${basename} root=${linux_root_device_thisversion} ro ${args}
EOF
  if [ "x$5" != "xquiet" ]; then
    cat << EOF
	echo	'$(gettext_quoted "Loading initial ramdisk ...")'
EOF
  fi
  if test -n "${initrd}" ; then
    cat << EOF
	initrd	${rel_dirname}/${initrd}
EOF
  fi
  cat << EOF
}
EOF
}

list=`for i in /boot/vmlinu[xz]-* /vmlinu[xz]-* ; do
        if grub_file_is_not_garbage "$i" ; then echo -n "$i " ; fi
      done`
prepare_boot_cache=

while [ "x$list" != "x" ] ; do
  linux=`version_find_latest $list`
  echo "Found linux image: $linux" >&2
  basename=`basename $linux`
  dirname=`dirname $linux`
  rel_dirname=`make_system_path_relative_to_its_root $dirname`
  version=`echo $basename | sed -e "s,^[^0-9]*-,,g"`
  alt_version=`echo $version | sed -e "s,\.old$,,g"`
  linux_root_device_thisversion="${LINUX_ROOT_DEVICE}"
# User-added variable
  codename="`lsb_release -cs`"
  codename="`echo $codename | tr [hjkl] [HJKL]`"
  version_no_generic="`echo ${version} | cut -d "-" -f 1-2`"

  initrd=
  for i in "initrd.img-${version}" "initrd-${version}.img" \
	   "initrd-${version}" "initrd.img-${alt_version}" \
	   "initrd-${alt_version}.img" "initrd-${alt_version}"; do
    if test -e "${dirname}/${i}" ; then
      initrd="$i"
      break
    fi
  done
  if test -n "${initrd}" ; then
    echo "Found initrd image: ${dirname}/${initrd}" >&2
  else
    # "UUID=" magic is parsed by initrds.  Since there's no initrd, it can't work here.
    linux_root_device_thisversion=${GRUB_DEVICE}
  fi

  linux_entry "${OS}" false\
      "${GRUB_CMDLINE_LINUX} ${GRUB_CMDLINE_EXTRA} ${GRUB_CMDLINE_LINUX_DEFAULT}" \
      quiet
  if [ "x${GRUB_DISABLE_LINUX_RECOVERY}" != "xtrue" ]; then
    linux_entry "${OS}" true\
	"single ${GRUB_CMDLINE_LINUX}"
  fi

  list=`echo $list | tr ' ' '\n' | grep -vx $linux | tr '\n' ' '`
done
```

---

### Post by drs305 on 2010-06-20
Added: Go to Post 112 for the solution to *ssaint04's* request.

I imported your 10_linux file into my system and ran update-grub. It generated an error message about "quiet" but the problem really lies in this line:
> 
linux_entry "${OS}" false\


Change it to the following, adding a space between *false* and *\*. Then run "sudo update-grub" and see if that fixes things for you:
> 
linux_entry "${OS}" false \


---

### Post by ssaint04 on 2010-06-20
> **drs305 said:**
> I imported your 10_linux file into my system and ran update-grub. It generated an error message about "quiet" but the problem really lies in this line:


Change it to the following, adding a space between *false* and *\*. Then run "sudo update-grub" and see if that fixes things for you:

Well, it didn't work. I still get "Ubuntu, with Linux false"

On a whim, I tried removing the "false"

The "false" went away, replaced by "quiet splash"

So, I tried removing the "quiet" on the line following the "false"

It hated that. Made the menu say "Ubuntu, with Linux (recovery mode)... which, well, it wasn't recovery mode when it booted.


I'm even more :confused: than I was before!

---

### Post by drs305 on 2010-06-20
ssaint04,

Here is your modified file which produces "Ubuntu " for the 10_linux entry. I kept getting error messages by removing the *${version}* entry so I just made it a blank instead. (I'm not a scripter, so I can't say it's pretty, but it seems to work.)

The lines in bold are the ones I changed, but the easiest way to incorporate this is to just copy/paste.

```

#! /bin/sh -e

# grub-mkconfig helper script.
# Copyright (C) 2006,2007,2008,2009,2010  Free Software Foundation, Inc.
#
# GRUB is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# GRUB is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with GRUB.  If not, see <http://www.gnu.org/licenses/>.

prefix=/usr
exec_prefix=${prefix}
bindir=${exec_prefix}/bin
libdir=${exec_prefix}/lib
. ${libdir}/grub/grub-mkconfig_lib

export TEXTDOMAIN=grub
export TEXTDOMAINDIR=@LOCALEDIR@

CLASS="--class gnu-linux --class gnu --class os"

if [ "x${GRUB_DISTRIBUTOR}" = "x" ] ; then
  OS=GNU/Linux
else
  OS="${GRUB_DISTRIBUTOR}"
  CLASS="--class $(echo ${GRUB_DISTRIBUTOR} | tr '[A-Z]' '[a-z]' | cut -d' ' -f1) ${CLASS}"
fi

# loop-AES arranges things so that /dev/loop/X can be our root device, but
# the initrds that Linux uses don't like that.
case ${GRUB_DEVICE} in
  /dev/loop/*|/dev/loop[0-9])
    GRUB_DEVICE=`losetup ${GRUB_DEVICE} | sed -e "s/^[^(]*(\([^)]\+\)).*/\1/"`
    # We can't cope with devices loop-mounted from files here.
    case ${GRUB_DEVICE} in
      /dev/*) ;;
      *) exit 0 ;;
    esac
  ;;
esac

if [ "x${GRUB_DEVICE_UUID}" = "x" ] || [ "x${GRUB_DISABLE_LINUX_UUID}" = "xtrue" ] \
    || ! test -e "/dev/disk/by-uuid/${GRUB_DEVICE_UUID}" \
    || [ "`grub-probe -t abstraction --device ${GRUB_DEVICE} | sed -e 's,.*\(lvm\).*,\1,'`" = "lvm"  ] ; then
  LINUX_ROOT_DEVICE=${GRUB_DEVICE}
else
  LINUX_ROOT_DEVICE=UUID=${GRUB_DEVICE_UUID}
fi

# add crashkernel option if we have the required tools
if [ -x "/usr/bin/makedumpfile" ] && [ -x "/sbin/kexec" ]; then
    GRUB_CMDLINE_EXTRA="$GRUB_CMDLINE_EXTRA crashkernel=384M-2G:64M,2G-:128M"
fi

linux_entry ()
{
  os="$1"
  version="$2"
  recovery="$3"
  args="$4"
[b]  if ${recovery} ; then
    title="$(gettext_quoted "%s %s (recovery mode)")"
  else
    title="$(gettext_quoted "%s %s")"
  fi[/b]
  printf "menuentry '${title}' ${CLASS} {\n" "${os}" "${version}"
  cat << EOF
	recordfail
EOF
  save_default_entry | sed -e "s/^/\t/"

  if [ "x$GRUB_GFXPAYLOAD_LINUX" != x ]; then
	  cat << EOF
	set gfxpayload=$GRUB_GFXPAYLOAD_LINUX
EOF
  fi

  if [ -z "${prepare_boot_cache}" ]; then
    prepare_boot_cache="$(prepare_grub_to_access_device ${GRUB_DEVICE_BOOT} | sed -e "s/^/\t/")"
  fi
  printf '%s\n' "${prepare_boot_cache}"
  if [ "x$5" != "xquiet" ]; then
    cat << EOF
	echo	'$(printf "$(gettext_quoted "Loading Linux %s ...")" ${version})'
EOF
  fi
  cat << EOF
	linux	${rel_dirname}/${basename} root=${linux_root_device_thisversion} ro ${args}
EOF
  if [ "x$5" != "xquiet" ]; then
    cat << EOF
	echo	'$(gettext_quoted "Loading initial ramdisk ...")'
EOF
  fi
  if test -n "${initrd}" ; then
    cat << EOF
	initrd	${rel_dirname}/${initrd}
EOF
  fi
  cat << EOF
}
EOF
}

list=`for i in /boot/vmlinu[xz]-* /vmlinu[xz]-* ; do
        if grub_file_is_not_garbage "$i" ; then echo -n "$i " ; fi
      done`
prepare_boot_cache=

while [ "x$list" != "x" ] ; do
  linux=`version_find_latest $list`
  echo "Found linux image: $linux" >&2
  basename=`basename $linux`
  dirname=`dirname $linux`
  rel_dirname=`make_system_path_relative_to_its_root $dirname`
[b]#  version=`echo $basename | sed -e "s,^[^0-9]*-,,g"`
   version=``[/b]
  alt_version=`echo $version | sed -e "s,\.old$,,g"`
  linux_root_device_thisversion="${LINUX_ROOT_DEVICE}"
# User-added variable
  codename="`lsb_release -cs`"
  codename="`echo $codename | tr [hjkl] [HJKL]`"
  version_no_generic="`echo ${version} | cut -d "-" -f 1-2`"

  initrd=
  for i in "initrd.img-${version}" "initrd-${version}.img" \
	   "initrd-${version}" "initrd.img-${alt_version}" \
	   "initrd-${alt_version}.img" "initrd-${alt_version}"; do
    if test -e "${dirname}/${i}" ; then
      initrd="$i"
      break
    fi
  done
  if test -n "${initrd}" ; then
    echo "Found initrd image: ${dirname}/${initrd}" >&2
  else
    # "UUID=" magic is parsed by initrds.  Since there's no initrd, it can't work here.
    linux_root_device_thisversion=${GRUB_DEVICE}
  fi

**  linux_entry "${OS}" "${version}" false\**
      "${GRUB_CMDLINE_LINUX} ${GRUB_CMDLINE_EXTRA} ${GRUB_CMDLINE_LINUX_DEFAULT}" \
      quiet
  if [ "x${GRUB_DISABLE_LINUX_RECOVERY}" != "xtrue" ]; then
    linux_entry "${OS}" true\
	"single ${GRUB_CMDLINE_LINUX}"
  fi

  list=`echo $list | tr ' ' '\n' | grep -vx $linux | tr '\n' ' '`
done

```

---

### Post by ssaint04 on 2010-06-20
It worked!


You sir, are awesome! 



\\:D/

(And a better scripter than I am!)

---

### Post by COKEDUDE on 2010-06-22
drs305 could you explain how changing what you changed fixed the problem? I would like to learn.

---

### Post by drs305 on 2010-06-22
> **COKEDUDE said:**
> drs305 could you explain how changing what you changed fixed the problem? I would like to learn.

I would love to, but I am not a scripting wizard so I can't use the example as the way it *should* be done. In fact, I'm almost positive it *isn't* the way it should be done, it just worked with some trial and error.

The title line had to be changed to eliminate the "with Linux..." section.
From:
> title="$(gettext_quoted "%s, with Linux %s")"
To:
> title="$(gettext_quoted "%s %s")"
In an unedited file, the actual menu entry is created based on this line:
>   linux_entry "${OS}" "${version}" false \
Since the user wanted the OS (Ubuntu), but not the version (2.6.32-...), I thought I could just remove the "${version}" from the line, but when I did this it produced errors, so I fell back to just changing the version value to a space by making this change (commenting the original line that created the 'version' information and making the value always be a space).
> #  version=`echo $basename | sed -e "s,^[^0-9]*-,,g"`
   version=``


I don't want to get into much more detail. Wanting to learn how scripting works is an admirable thing. Trying to learn scripting from my efforts is something neither I nor anyone who has seen my efforts would recommend. ;-)

---

### Post by GeoPirate on 2010-07-02
Ok, I've read through this thread and several others, but I can't seem to find how to do what I want to do.  On my system I have the stable version of ubuntu on sda1 and the testing version on sda3, is there a way for me to have grub 2 just set the title based on the location instead of off the codename or kernel.  So that in my case it would take anything it finds on /dev/sda1 and put the title as "Stable" and then anything it finds on /dev/sda3 and put the title as "Testing"?

---

### Post by drs305 on 2010-07-03
> **GeoPirate said:**
> On my system I have the stable version of ubuntu on sda1 and the testing version on sda3, is there a way for me to have grub 2 just set the title based on the location instead of off the codename or kernel.  So that in my case it would take anything it finds on /dev/sda1 and put the title as "Stable" and then anything it finds on /dev/sda3 and put the title as "Testing"?

I've tweaked the 10_linux file and have come up with a result which should work for you. I've had to modify several different sections of the file. The lines with a ## are originals, those within ##### are the new lines.

I didn't take your request for the title to be "Stable" literally, since without a version number you couldn't tell the difference between Stable 2.6.32-32 and Stable 2.6.32-33. If you don't want the version number - just "Stable - edit the section in red.

Backup your current /etc/grub.d/10_linux, replace it with the code below, then run "sudo update-grub".

```
#! /bin/sh -e

# grub-mkconfig helper script.
# Copyright (C) 2006,2007,2008,2009,2010  Free Software Foundation, Inc.
#
# GRUB is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# GRUB is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with GRUB.  If not, see <http://www.gnu.org/licenses/>.

prefix=/usr
exec_prefix=${prefix}
bindir=${exec_prefix}/bin
libdir=${exec_prefix}/lib
. ${libdir}/grub/grub-mkconfig_lib

export TEXTDOMAIN=grub
export TEXTDOMAINDIR=@LOCALEDIR@

CLASS="--class gnu-linux --class gnu --class os"

if [ "x${GRUB_DISTRIBUTOR}" = "x" ] ; then
  OS=GNU/Linux
else
  OS="${GRUB_DISTRIBUTOR}"
  CLASS="--class $(echo ${GRUB_DISTRIBUTOR} | tr '[A-Z]' '[a-z]' | cut -d' ' -f1) ${CLASS}"
fi

# loop-AES arranges things so that /dev/loop/X can be our root device, but
# the initrds that Linux uses don't like that.
case ${GRUB_DEVICE} in
  /dev/loop/*|/dev/loop[0-9])
    GRUB_DEVICE=`losetup ${GRUB_DEVICE} | sed -e "s/^[^(]*(\([^)]\+\)).*/\1/"`
    # We can't cope with devices loop-mounted from files here.
    case ${GRUB_DEVICE} in
      /dev/*) ;;
      *) exit 0 ;;
    esac
  ;;
esac

if [ "x${GRUB_DEVICE_UUID}" = "x" ] || [ "x${GRUB_DISABLE_LINUX_UUID}" = "xtrue" ] \
    || ! test -e "/dev/disk/by-uuid/${GRUB_DEVICE_UUID}" \
    || [ "`grub-probe -t abstraction --device ${GRUB_DEVICE} | sed -e 's,.*\(lvm\).*,\1,'`" = "lvm"  ] ; then
  LINUX_ROOT_DEVICE=${GRUB_DEVICE}
else
  LINUX_ROOT_DEVICE=UUID=${GRUB_DEVICE_UUID}
fi

# add crashkernel option if we have the required tools
if [ -x "/usr/bin/makedumpfile" ] && [ -x "/sbin/kexec" ]; then
    GRUB_CMDLINE_EXTRA="$GRUB_CMDLINE_EXTRA crashkernel=384M-2G:64M,2G-:128M"
fi

linux_entry ()
{
  os="$1"
  version="$2"
  recovery="$3"
  args="$4"
##  if ${recovery} ; then
##    title="$(gettext_quoted "%s, with Linux %s (recovery mode)")"
##  else
##    title="$(gettext_quoted "%s, with Linux %s")"
##  fi
##### New
  if ${recovery} ; then
    title="$(gettext_quoted "%s %s (recovery mode)")"
  else
    title="$(gettext_quoted "%s %s")"
  fi
##### End New

  printf "menuentry '${title}' ${CLASS} {\n" "${os}" "${version}"
  cat << EOF
	recordfail
EOF
  save_default_entry | sed -e "s/^/\t/"

  if [ "x$GRUB_GFXPAYLOAD_LINUX" != x ]; then
	  cat << EOF
	set gfxpayload=$GRUB_GFXPAYLOAD_LINUX
EOF
  fi

  if [ -z "${prepare_boot_cache}" ]; then
    prepare_boot_cache="$(prepare_grub_to_access_device ${GRUB_DEVICE_BOOT} | sed -e "s/^/\t/")"
  fi
  printf '%s\n' "${prepare_boot_cache}"
  if [ "x$5" != "xquiet" ]; then
    cat << EOF
	echo	'$(printf "$(gettext_quoted "Loading Linux %s ...")" ${version})'
EOF
  fi
  cat << EOF
	linux	${rel_dirname}/${basename} root=${linux_root_device_thisversion} ro ${args}
EOF
  if [ "x$5" != "xquiet" ]; then
    cat << EOF
	echo	'$(gettext_quoted "Loading initial ramdisk ...")'
EOF
  fi
  if test -n "${initrd}" ; then
    cat << EOF
	initrd	${rel_dirname}/${initrd}
EOF
  fi
  cat << EOF
}
EOF
}

list=`for i in /boot/vmlinu[xz]-* /vmlinu[xz]-* ; do
        if grub_file_is_not_garbage "$i" ; then echo -n "$i " ; fi
      done`
prepare_boot_cache=

while [ "x$list" != "x" ] ; do
  linux=`version_find_latest $list`
  echo "Found linux image: $linux" >&2
  basename=`basename $linux`
  dirname=`dirname $linux`
  rel_dirname=`make_system_path_relative_to_its_root $dirname`
  [COLOR="Red"]version=`echo $basename | sed -e "s,^[^0-9]*-,,g"`[/COLOR]
#####
# [COLOR="Red"]version=" "[/COLOR]
#####
  alt_version=`echo $version | sed -e "s,\.old$,,g"`
  linux_root_device_thisversion="${LINUX_ROOT_DEVICE}"

  initrd=
  for i in "initrd.img-${version}" "initrd-${version}.img" \
	   "initrd-${version}" "initrd.img-${alt_version}" \
	   "initrd-${alt_version}.img" "initrd-${alt_version}"; do
    if test -e "${dirname}/${i}" ; then
      initrd="$i"
      break
    fi
  done
  if test -n "${initrd}" ; then
    echo "Found initrd image: ${dirname}/${initrd}" >&2
  else
    # "UUID=" magic is parsed by initrds.  Since there's no initrd, it can't work here.
    linux_root_device_thisversion=${GRUB_DEVICE}
  fi

##  linux_entry "${OS}" "${version}" false \
##      "${GRUB_CMDLINE_LINUX} ${GRUB_CMDLINE_EXTRA} ##${GRUB_CMDLINE_LINUX_DEFAULT}" \
##      quiet
##  if [ "x${GRUB_DISABLE_LINUX_RECOVERY}" != "xtrue" ]; then
##    linux_entry "${OS}" "${version}" true \
##	"single ${GRUB_CMDLINE_LINUX}"
##  fi
##### New
if [ ${GRUB_DEVICE} = "/dev/sda1" ]; then
  linux_entry "Stable" "${version}" false \
      "${GRUB_CMDLINE_LINUX} ${GRUB_CMDLINE_EXTRA} ${GRUB_CMDLINE_LINUX_DEFAULT}" \
      quiet
  if [ "x${GRUB_DISABLE_LINUX_RECOVERY}" != "xtrue" ]; then
    linux_entry "Stable" "${version}" true \
	"single ${GRUB_CMDLINE_LINUX}"
  fi
else
  linux_entry "${OS}" "${version}" false \
      "${GRUB_CMDLINE_LINUX} ${GRUB_CMDLINE_EXTRA} ${GRUB_CMDLINE_LINUX_DEFAULT}" \
      quiet
  if [ "x${GRUB_DISABLE_LINUX_RECOVERY}" != "xtrue" ]; then
    linux_entry "${OS}" "${version}" true \
	"single ${GRUB_CMDLINE_LINUX}"
  fi
fi
##### End New
  list=`echo $list | tr ' ' '\n' | grep -vx $linux | tr '\n' ' '`
done

```

I'll work up the changes to the sda3 "Testing" entry (30_os-prober) when I have time.

---

### Post by drs305 on 2010-07-04
The "Testing" entry is pretty easy.

Backup 30_os-prober and remove the executable bit so the backup won't run. Open for editing.
```

sudo cp /etc/grub.d/30_os-prober /etc/grub.d/30_os-prober.bak
sudo chmod -x /etc/grub.d/30_os-prober.bak
gksu gedit /etc/grub.d/30_os-prober &
```
Save the file, then run:
```
sudo update-grub
```

Find this section (approximately line 170) and add the bold dark red text:
>     ;;
    linux)
      LINUXPROBED="`linux-boot-prober ${DEVICE} 2> /dev/null | tr ' ' '^' | paste -s -d ' '`"
      prepare_boot_cache=

      for LINUX in ${LINUXPROBED} ; do
        LROOT="`echo ${LINUX} | cut -d ':' -f 1`"
        LBOOT="`echo ${LINUX} | cut -d ':' -f 2`"
        LLABEL="`echo ${LINUX} | cut -d ':' -f 3 | tr '^' ' '`"
        LKERNEL="`echo ${LINUX} | cut -d ':' -f 4`"
        LINITRD="`echo ${LINUX} | cut -d ':' -f 5`"
        LPARAMS="`echo ${LINUX} | cut -d ':' -f 6- | tr '^' ' '`"

[B][COLOR="DarkRed"]
##### Add this
  if [ ${DEVICE} = "/dev/sda3" ] ; then
    LLABEL="Testing"
  fi
##### End Add
[/COLOR][/B]

Once again, the note about this not displaying kernel version, so multiple kernels would have the same name. This can be changed to include the kernel if desired.
If you don't want the "on /dev/sda3" in the title, go to this section a bit further down and remove the bold text:
> 
        cat << EOF
menuentry "${LLABEL} **(on ${DEVICE})**" {
EOF


---

### Post by Tikhon03 on 2010-07-06
I have a comment on the code for one of your tweaks, and I have one of my own tweaks to offer.  When I tried using
```
sudo cat /boot/grub/grub.cfg | grep "menuentry" | cut -d '"' -f 2
```
to get the menu entries, it truncated my list! :( I tried using
```
sudo cat /boot/grub/grub.cfg | grep "menuentry"
```
instead, and got the full list. :) Naturally you have to use a little common sense about what part of the title to take, and whether it corresponds to LONGNAME (Windows) or LLABEL (Linux).

Now here is my own tweak, with appropriate context. I have recently set up my computer to have 4 linux distros on it: Kubuntu, Fedora, Mandriva, and OpenSuse.  Kubuntu is in charge of the boot loader.  When Fedora was loaded the screen would shimmer and flicker.  The solution I found in the online documentation was to add "nomodeset" to the Kernel Parameters.  Doing this in GRUB is easy, but what about GRUB 2? Well the options seem to be

a) add a custom menu entry, and remove the autmatically generated one for Fedora.

b) change the 30_os-prober script to adjust the menu entry already generated.

I did not like the idea of adding another menu entry for fedora without removing the automatically generated one, because that entry would be effectively useless. Who wants to look at a shimmering screen??  I decided that option b) was easier.  So in the 30_os-prober immediately after the lines

```
for LINUX in ${LINUXPROBED} ; do
        LROOT="`echo ${LINUX} | cut -d ':' -f 1`"
        LBOOT="`echo ${LINUX} | cut -d ':' -f 2`"
        LLABEL="`echo ${LINUX} | cut -d ':' -f 3 | tr '^' ' '`"
        LKERNEL="`echo ${LINUX} | cut -d ':' -f 4`"
        LINITRD="`echo ${LINUX} | cut -d ':' -f 5`"
        LPARAMS="`echo ${LINUX} | cut -d ':' -f 6- | tr '^' ' '`"

        if [ -z "${LLABEL}" ] ; then
          LLABEL="${LONGNAME}"
        fi

	if [ "${LROOT}" != "${LBOOT}" ]; then
	  LKERNEL="${LKERNEL#/boot}"
	  LINITRD="${LINITRD#/boot}"
	fi
```

I added the lines

```
if [ "${LKERNEL}" = "/boot/vmlinuz-2.6.33.3-85.fc13.i686" ]; then
          LPARAMS="root=/dev/sda8 nomodeset"
fi
```

"root=/dev/sda8" is what LPARAMS was before the new parameter "nomodeset" was added. Then I ran update-grub to generate the grub.cfg file.  Sure enough it worked!  Now when I select the Fedora menu entry, the screen is normal. :D

---

### Post by drs305 on 2010-07-06
Tikhon03,

Nice. The LPARAMS is something I haven't played with much. 

The "nomodeset" option as with others is normally be placed on the "GRUB_CMDLINE_LINUX_DEFAULT=" line of /etc/default/grub *for your main Linux OS*, but to get it into your Fedora OS your method works well.

I do note that your tweak is active for a specific kernel. You could also make the LPARAMS line a condition of the OS being on sda8 (if only Fedora is on sda8 or use the "cut" command to add *nomodeset* to any kernel with the "fc13.i686" designation (if that is Fedora-specific).

As to the "cat" command from the original post, the command is located in and only referenced in the Windows section of the guide. On my machines the command provides the complete Windows title without the quotes, which was what I wanted. However, I don't have Vista or 7 so their titles might be a bit different and the command may produce undesired results. 

If the command improperly truncates Windows titles I'll need to change it. If it truncates other OS's I'm not as concerned. I could expand it to grep "Windows" as well so only Windows entries appear, without quotes:
```
grep "menuentry" /boot/grub/grub.cfg | grep "Windows" | cut -d '"' -f 2
```

---

### Post by BryanFRitt on 2010-07-11
If you want to to figure out what LONGNAME is for changing a menu entry, and if it's being changed try something like this:

edit /etc/grub.d/30_os-prober like this, probably around line 139 ish
```
#/etc/grub.d/30_os-prober
#http://ubuntuforums.org/showthread.php?t=1287602
#  if [ -z "${LONGNAME}" ] ; then
#    LONGNAME="${LABEL}"
#  fi
#see /boot/grub/grub.cfg for the output of these lines after a [FONT="Courier New"]sudo update-grub2[/FONT], if not commented out
#the '#' in the echo is so that this doesn't give an error if you accidentally(or decide to) leave it
[B]echo '#${LONGNAME} was'
echo "#${LONGNAME}"[/B]
 if [ "${LONGNAME}" = "*LONGNAME text to be replaced*" ] ; then
   LONGNAME="*LONGNAME replacement text*"
 elif [ -z "${LONGNAME}" ] ; then
   LONGNAME="${LABEL}"
 fi
[B]echo '#${LONGNAME} is now'
echo "#${LONGNAME}"
```[/B]
then run [FONT="Courier New"]sudo update-grub2[/FONT] and see the output in /boot/grub/grub.cfg

---

### Post by drs305 on 2010-07-11
Since I often try to provide solutions in this thread and use the "cut" command, I like to know the format of the basic variables in 10_linux and 30_os-prober. Here is a list I keep of the standard output formats:

**[SIZE="3"]VARIABLES:[/SIZE]**

**10_linux:**
**linux: **		/boot/vmlinuz-2.6.32-22-generic 
**basename:** 	vmlinuz-2.6.32-22-generic 
**dirname:** 	/boot 
**version:** 		2.6.32-22-generic 
**alt_version:** 	2.6.32-22-generic 
**linux_root_device_thisversion:** 	UUID=c5163c70-4f7-4034-a218-5dae03b07eed

**30_os-prober:**
**DEVICE:**   	/dev/sda9 
**LONGNAME:**  	Ubuntu 8.10 (8.10) 
**OS: **		/dev/sda9:Ubuntu^8.10^(8.10):Ubuntu:linux 
**LABEL:**		Ubuntu 
**BOOT: **		linux 
**LROOT: **		/dev/sda9 
**LINUX:** 		/dev/sda9:/dev/sda9:Ubuntu^8.10,^kernel^2.6.27-9-generic:/boot/vmlinuz-2.6.27-9-generic:/boot/initrd.img-2.6.27-9-generic:root=UUID=ba83d184-705e-4115-9d42-0823c698a77^ro^splash^quiet 
**LLABEL: **		Ubuntu 8.10, kernel 2.6.27-9-generic 
**LKERNEL:** 	/boot/vmlinuz-2.6.27-9-generic 
**LINITRD: **		/boot/initrd.img-2.6.27-9-generic 
**LPARAMS:** 	root=UUID=ba83d184-705e-4115-9d42-0823c698a77 ro splash quiet

---

### Post by Zens on 2010-07-21
> **CharlesA said:**
> Yeah, you should remove "false"

It should looks like this:

```
  linux_entry "${OS} ${version_no_generic}" \
```The problem I had was if I updated the variable with the name I wanted, it would leave off "recovery mode" so I did a quick and dirty workaround:

I had to edit /boot/grub/menu.lst on the BT4 install and then running "update-grub" from Ubuntu 9.10.

Original menu.lst:

```
title        Ubuntu 8.10, kernel 2.6.30.9
uuid        a76c7835-eb6f-459f-a891-496f16bc00eb
kernel        /boot/vmlinuz-2.6.30.9 root=UUID=a76c7835-eb6f-459f-a891-496f16bc00eb ro vga=0x317 
initrd        /boot/initrd.img-2.6.30.9
quiet

title        Ubuntu 8.10, kernel 2.6.30.9 (recovery mode)
uuid        a76c7835-eb6f-459f-a891-496f16bc00eb
kernel        /boot/vmlinuz-2.6.30.9 root=UUID=a76c7835-eb6f-459f-a891-496f16bc00eb ro  single
initrd        /boot/initrd.img-2.6.30.9

title        Ubuntu 8.10, memtest86+
uuid        a76c7835-eb6f-459f-a891-496f16bc00eb
kernel        /boot/memtest86+.bin
quiet

```Edited menu.lst:

```
title        **Backtrack 4 Final (2.6.30.9)**
uuid        8ce79a61-7653-4799-950e-bca17e0b5b77
kernel        /boot/vmlinuz-2.6.30.9 root=UUID=8ce79a61-7653-4799-950e-bca17e0b5b77 ro quiet splash 
initrd        /boot/initrd.img-2.6.30.9
quiet

title        **Backtrack 4 Final (.6.30.92)** (recovery mode)
uuid        8ce79a61-7653-4799-950e-bca17e0b5b77
kernel        /boot/vmlinuz-2.6.30.9 root=UUID=8ce79a61-7653-4799-950e-bca17e0b5b77 ro  single
initrd        /boot/initrd.img-2.6.30.9

#title        Ubuntu 8.10, memtest86+
#uuid        8ce79a61-7653-4799-950e-bca17e0b5b77
kernel        /boot/memtest86+.bin
quiet

```Here is what my Grub2 menu looks like now:

```
Karmic (2.6.31-20)
Karmic (2.6.31-20) (recovery mode)
Karmic (2.6.31-14)
Karmic (2.6.31-14) (recovery mode)
Windows 7 Professional
Backtrack 4 Final (2.6.30.9)
Backtrack 4 Final (2.6.30.9) (recovery mode)
```Much, much cleaner.

Thank you so much for sharing that!

I was able to rename BT4 through that simple edit. No needing to miss with Grub 2 files on Ubuntu ;).

---

### Post by corrytonapple on 2010-09-25
Works great, and the link to a custom menu is great too! Thanks
:guitar:

---

### Post by alababi on 2010-10-31
help, I got a huge problem with this tweaking.

I was following the instruction in post 112. However, I think I've missed some lines so I'm encountering a huge problem. After restarting to see the result, I didnt see the Ubuntu entry anymore, only the recovery mode and the windows left. Now I couldn't log on to Ubuntu.

How can I log on to ubuntu in recovery mode to change back the files I just edited? Or should I reinstall Ubuntu ?

---

### Post by Agent.Logic_ on 2010-10-31
> **alababi said:**
> help, I got a huge problem with this tweaking.

I was following the instruction in post 112. However, I think I've missed some lines so I'm encountering a huge problem. After restarting to see the result, I didnt see the Ubuntu entry anymore, only the recovery mode and the windows left. Now I couldn't log on to Ubuntu.

How can I log on to ubuntu in recovery mode to change back the files I just edited? Or should I reinstall Ubuntu ?
You could boot in recovery mode and edit the grub file using nano. It has a very friendly interface and it is one of the easiest command line text editing programs out there. Or, if you had made a backup of your grub configuration before you started editing it, you can restore it from recovery mode. You don't have to go to the trouble of reinstalling Ubuntu, it's probably just a small error and easily fixable. Just post the contents of your configuration file here so we could see what went wrong (use a usb stick to copy the contents of the grub configuration file, then boot into Windows to post it here).

---

### Post by alababi on 2010-10-31
> **Agent.Logic_ said:**
> You could boot in recovery mode and edit the grub file using nano. It has a very friendly interface and it is one of the easiest command line text editing programs out there. Or, if you had made a backup of your grub configuration before you started editing it, you can restore it from recovery mode. You don't have to go to the trouble of reinstalling Ubuntu, it's probably just a small error and easily fixable. Just post the contents of your configuration file here so we could see what went wrong (use a usb stick to copy the contents of the grub configuration file, then boot into Windows to post it here).
Please elucidate the nano stuff for me. As you can see, I'm just a newbie to ubuntu. When I chose the recovery mode entry, all I saw was black screen with commands, similar to a full screen size terminal.
I just need to be able to log on to Ubuntu to set everything as default, I saved the original commands which I changed as comments.

---

### Post by Agent.Logic_ on 2010-10-31
> **alababi said:**
> Please elucidate the nano stuff for me. As you can see, I'm just a newbie to ubuntu. When I chose the recovery mode entry, all I saw was black screen with commands, similar to a full screen size terminal.
I just need to be able to log on to Ubuntu to set everything as default, I saved the original commands which I changed as comments.
Okay, I'll walk you through. 

When you boot into recovery mode, a lot of lines will fly by you (don't get bogged down, it is impossible to keep up with and most of it is just information about what is loading currently, ignorable warnings etc.) After everything has finished loading, you will be a few options, just scroll down with your **down arrow key** and choose "**drop to root shell prompt**."

[LIST=1]
[*]Type ```
nano /etc/grub.d/10_linux
```seeing that you edited that file according to post #112. Please do tell if you edited any other grub related configuration file.

[*]Just remove the edits on post #112 and uncomment the lines you commented out originally.

[*]Save it by pressing ctrl + O (Write Out) and exit by pressing ctrl + X.

[*]Type in ```
update-grub
``` and when it is done, type in ```
update-initramfs -u
```

[*]Reboot by typing ```
reboot
```
[/LIST]

Hopefully, this should fix it. If you are not sure anymore that the 10_linux file was restored to its original self, here is the untouched version of the 10_linux file:

```
#! /bin/sh -e

# grub-mkconfig helper script.
# Copyright (C) 2006,2007,2008,2009,2010  Free Software Foundation, Inc.
#
# GRUB is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# GRUB is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with GRUB.  If not, see <http://www.gnu.org/licenses/>.

prefix=/usr
exec_prefix=${prefix}
bindir=${exec_prefix}/bin
libdir=${exec_prefix}/lib
. ${libdir}/grub/grub-mkconfig_lib

export TEXTDOMAIN=grub
export TEXTDOMAINDIR=@LOCALEDIR@

CLASS="--class gnu-linux --class gnu --class os"

if [ "x${GRUB_DISTRIBUTOR}" = "x" ] ; then
  OS=GNU/Linux
else
  OS="${GRUB_DISTRIBUTOR}"
  CLASS="--class $(echo ${GRUB_DISTRIBUTOR} | tr '[A-Z]' '[a-z]' | cut -d' ' -f1) ${CLASS}"
fi

# loop-AES arranges things so that /dev/loop/X can be our root device, but
# the initrds that Linux uses don't like that.
case ${GRUB_DEVICE} in
  /dev/loop/*|/dev/loop[0-9])
    GRUB_DEVICE=`losetup ${GRUB_DEVICE} | sed -e "s/^[^(]*(\([^)]\+\)).*/\1/"`
    # We can't cope with devices loop-mounted from files here.
    case ${GRUB_DEVICE} in
      /dev/*) ;;
      *) exit 0 ;;
    esac
  ;;
esac

if [ "x${GRUB_DEVICE_UUID}" = "x" ] || [ "x${GRUB_DISABLE_LINUX_UUID}" = "xtrue" ] \
    || ! test -e "/dev/disk/by-uuid/${GRUB_DEVICE_UUID}" \
    || [ "`grub-probe -t abstraction --device ${GRUB_DEVICE} | sed -e 's,.*\(lvm\).*,\1,'`" = "lvm"  ] ; then
  LINUX_ROOT_DEVICE=${GRUB_DEVICE}
else
  LINUX_ROOT_DEVICE=UUID=${GRUB_DEVICE_UUID}
fi

# add crashkernel option if we have the required tools
if [ -x "/usr/bin/makedumpfile" ] && [ -x "/sbin/kexec" ]; then
    GRUB_CMDLINE_EXTRA="$GRUB_CMDLINE_EXTRA crashkernel=384M-2G:64M,2G-:128M"
fi

linux_entry ()
{
  os="$1"
  version="$2"
  recovery="$3"
  args="$4"
  if ${recovery} ; then
    title="$(gettext_quoted "%s, with Linux %s (recovery mode)")"
  else
    title="$(gettext_quoted "%s, with Linux %s")"
  fi
  printf "menuentry '${title}' ${CLASS} {\n" "${os}" "${version}"
  cat << EOF
	recordfail
EOF
  save_default_entry | sed -e "s/^/\t/"

  if [ "x$GRUB_GFXPAYLOAD_LINUX" != x ]; then
	  cat << EOF
	set gfxpayload=$GRUB_GFXPAYLOAD_LINUX
EOF
  fi

  if [ -z "${prepare_boot_cache}" ]; then
    prepare_boot_cache="$(prepare_grub_to_access_device ${GRUB_DEVICE_BOOT} | sed -e "s/^/\t/")"
  fi
  printf '%s\n' "${prepare_boot_cache}"
  if [ "x$5" != "xquiet" ]; then
    cat << EOF
	echo	'$(printf "$(gettext_quoted "Loading Linux %s ...")" ${version})'
EOF
  fi
  cat << EOF
	linux	${rel_dirname}/${basename} root=${linux_root_device_thisversion} ro ${args}
EOF
  if [ "x$5" != "xquiet" ]; then
    cat << EOF
	echo	'$(gettext_quoted "Loading initial ramdisk ...")'
EOF
  fi
  if test -n "${initrd}" ; then
    cat << EOF
	initrd	${rel_dirname}/${initrd}
EOF
  fi
  cat << EOF
}
EOF
}

list=`for i in /boot/vmlinu[xz]-* /vmlinu[xz]-* ; do
        if grub_file_is_not_garbage "$i" ; then echo -n "$i " ; fi
      done`
prepare_boot_cache=

while [ "x$list" != "x" ] ; do
  linux=`version_find_latest $list`
  echo "Found linux image: $linux" >&2
  basename=`basename $linux`
  dirname=`dirname $linux`
  rel_dirname=`make_system_path_relative_to_its_root $dirname`
  version=`echo $basename | sed -e "s,^[^0-9]*-,,g"`
  alt_version=`echo $version | sed -e "s,\.old$,,g"`
  linux_root_device_thisversion="${LINUX_ROOT_DEVICE}"

  initrd=
  for i in "initrd.img-${version}" "initrd-${version}.img" \
	   "initrd-${version}" "initrd.img-${alt_version}" \
	   "initrd-${alt_version}.img" "initrd-${alt_version}"; do
    if test -e "${dirname}/${i}" ; then
      initrd="$i"
      break
    fi
  done
  if test -n "${initrd}" ; then
    echo "Found initrd image: ${dirname}/${initrd}" >&2
  else
    # "UUID=" magic is parsed by initrds.  Since there's no initrd, it can't work here.
    linux_root_device_thisversion=${GRUB_DEVICE}
  fi

  linux_entry "${OS}" "${version}" false \
      "${GRUB_CMDLINE_LINUX} ${GRUB_CMDLINE_EXTRA} ${GRUB_CMDLINE_LINUX_DEFAULT}" \
      quiet
  if [ "x${GRUB_DISABLE_LINUX_RECOVERY}" != "xtrue" ]; then
    linux_entry "${OS}" "${version}" true \
	"single ${GRUB_CMDLINE_LINUX}"
  fi

  list=`echo $list | tr ' ' '\n' | grep -vx $linux | tr '\n' ' '`
done
```

---

### Post by alababi on 2010-10-31
@Agent Logic:

I just did as what you wrote but I stuck in step 3. After I changed the code, it didnt allow me to save the file. How can I overcome this ?

---

### Post by Agent.Logic_ on 2010-10-31
That's strange... you are logged in as root and that means you have complete access to the system. Nothing should stop you. Does it give you any error messages? When you press ctrl + O, a little dialog appears in the bottom of the screen asking "File name to write:" and you just have to press enter (to save it in the current file). Is this where you are stuck?

---

### Post by drs305 on 2010-10-31
@ alababi,

If you still have a Grub menu, but only see the "Recovery mode" option, highlight it and press "e". This should display the recovery mode menu commands.

Find the linux line - it should look something like this:
> 
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=1c4adc10-a208-4373-b842-9851a8421da9 ro [COLOR="DarkRed"]**single **[/COLOR]

Replace the word "single" with "quiet splash", then press CTRL-x to boot to the normal mode. 
> 
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=1c4adc10-a208-4373-b842-9851a8421da9 ro [COLOR="DarkRed"]**quiet splash **[/COLOR]


If successful, delete the current /etc/grub.d/10_linux file and  copy the 10_linux file posted by Agent.Logic_ or rename your backup file. To use a file browser as root, open nautilus with "gksu nautilus /etc/grub.d/"

After replacing the 10_linux file, run:
```
sudo update-grub
```

That should put things back the way they were.

---

### Post by weymouth on 2010-11-10
I am trying to get item 9 working (hide grub menu for a multi-OS system) but I have a different version of the 30_os-prober file. I am a new user and got this version of grub with my maverick install.

The major change I see is the defninition of a "make_timeout" script before the "adjust_timeout" script. I don't read scriptesse and I tried making what I hoped would be equivalent changes to this new script but nothing seems to have happened.

If I grab a copy of the old script and make the recommended changes will it mess anything up?

---

### Post by drs305 on 2010-11-10
> **weymouth said:**
> I am trying to get item 9 working (hide grub menu for a multi-OS system) but I have a different version of the 30_os-prober file. I am a new user and got this version of grub with my maverick install.

The major change I see is the defninition of a "make_timeout" script before the "adjust_timeout" script. I don't read scriptesse and I tried making what I hoped would be equivalent changes to this new script but nothing seems to have happened.

If I grab a copy of the old script and make the recommended changes will it mess anything up?

Have you tried just setting the "GRUB_TIMEOUT" value in /etc/default/grub to 0 ? I find in Maverick that is all it takes (after running update-grub).

If the "GRUB_TIMEOUT=0" does not work, does your system begin a countdown when the menu displays or does it await input from you? If there is no countdown it's possible that grub is detecting a 'recordfail' and will wait for input. We can change that behaviour as well but by a different method.

For now, if the TIMEOUT setting doesn't work, open /etc/grub.d/00_header and go to approximately line 238: 
```
gksu gedit +238 /etc/grub.d/00_header
```

Find this section and make the changes in **[COLOR="DarkRed"]dark red[/COLOR]**, then save the file and run "sudo update-grub".
> 
make_timeout ()
{
    cat << EOF
if [ "\${recordfail}" = 1 ]; then
  set timeout=-1
else
[B][COLOR="DarkRed"]
# Manually change timeout to 0
#  set timeout=${2} 
   set timeout=0
# End manual change
[/COLOR][/B]
fi
EOF
}


This should eliminate the menu display unless there is a "recordfail" event. It also preserves the ability to display the menu by holding down the SHIFT key during boot. Please let me know if this solution works for you.

I'll update the initial instructions after I've determined what has changed with the G2 scripts.

---

### Post by weymouth on 2010-11-10
Either I was unclear in the question or I don't understand the answer. :)

I don't want to bypass the grub menu, I want to hide it. So I want to boot the default OS unless I hold down the shift key, in which case the menu should come up allowing me to select the OS to boot.

In my experimentation, setting the GRUB_TIMEOUT=0 doesn't hide the menu - it bypasses it. Even if I'm holding down the shift key I go to the default boot option. How can I choose the OS in this case?

As way of explanation, this behavior is for a touch screen netbook. If I turn it on in tablet mode then I want win7 to come up without needing to type anything. (This also lets my family use the computer without having to wonder "what the $%&* is ubuntu?".) If I'm using the computer to ssh or something, then I will have the key board available and can hold down shift while booting to call up the grub menu.

---

### Post by drs305 on 2010-11-11
> **weymouth said:**
> Either I was unclear in the question or I don't understand the answer. :)

We may be talking cross purposes.  Here are the ways you should be able to get the grub menu to work:

(Single OS) Set the grub hidden timeout value to a positive integer. The screen will be blank and you can press any key during the countdown and the menu will appear for the time specified in the grub timeout. If no key is pressed, the grub default is booted. Note that if grub timeout is 0 you will not see the menu even if you press a key during the hidden timeout (it activates the display, but it displays it for 0 seconds so you don't see it).

If grub hidden timeout is not set or zero, the menu displays (on multiple-OS computers) for the value of grub timeout, then boots the default.

Do you want a blank screen for a period of time before the system selects the default?   Normally you would set the grub hidden timeout value to a positive number (or 0 for no delay at all) and set the grub timeout to 0. This sounds like what you want. The problem for you is that the way the 30_os-prober is written the hidden menu timeout options are limited to single OS systems. The script edits I recommend merely remove the condition that no other operating systems are found by 30_os-prober. (There are certain things such as a recordfail event that force the menu to appear.)

> 
In my experimentation, setting the GRUB_TIMEOUT=0 doesn't hide the menu - it bypasses it. Even if I'm holding down the shift key I go to the default boot option. How can I choose the OS in this case?

Grub is never 'bypassed' per se. It always boots to the whatever it's told the default is. The default may be a name, a menuentry number, or the last used OS.
There are times when the holding down the shift key doesn't work. *This may be what you were trying to fix. If so, read on for a solution.*

The way the Grub2 developers set up the keystatus check limits its function to specific circumstances. We can change the conditionals but it's easiest to just make sure it's checked by adding it to 00_header. If holding the shift key isn't working when you want it to, you can copy the following to the end of the /etc/grub.d/00_header file so that it is always available.

> 
	cat <<EOF
if [ "x\${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep$verbose --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
EOF


---

### Post by sweetleaf on 2010-11-20
> **drs305 said:**
> [B]7. [COLOR=DarkRed]CHANGING "Windows Recovery Environment (loader)" to "Windows Vista" 
or Any Other Windows Title in the 30_os-prober Section of grub.cfg[/COLOR][/B]


> **drs305 said:**
> 
if [ "$LONGNAME" = "Windows Recovery Environment (loader)" ] && [ "${DEVICE}" = "/dev/sda1" ] ; then
[color=red]${LONGNAME}=[/color]"Windows Vista"
fi


The syntax above is incorrect; it causes an error in 30_os-prober, which then fails to create any Windows entry in grub.cfg. 

The following code works:

> 
if [ "$LONGNAME" = "Windows Recovery Environment (loader)" ] && [ "${DEVICE}" = "/dev/sda1" ] ; then
[color=red]LONGNAME=[/color]"Windows Vista"
fi


Thanks for this tutorial. It solved my problem.

---

### Post by drs305 on 2010-11-21
> **sweetleaf said:**
> The syntax above is incorrect; it causes an error in 30_os-prober, which then fails to create any Windows entry in grub.cfg. 

Thanks for this tutorial. It solved my problem.

Thanks. Somewhere I messed it up during a revision update. Fixed.

---

### Post by n.hinton on 2010-11-24
Grub2 boots windows 98 in dos compatibility mode.

Have win98se on secondary master as it fully supports some devices Ubuntu doesn't (Aries scan it pro, pci smart modem, Lexmark printer/scanner x2250), Lucid is on primary master. Grub seamlessly booted windows using menu.lst entry:

```
title		Windows 95/98/Me
rootnoverify	(hd1,0)
savedefault
makeactive
chainloader	+1
map (hd0) (hd1)
map (hd1) (hd0)
```

Have updated grub to grub2 and cannot get it to boot windows without dos compatibility mode (which is no good for 2 of the above devices), it is not overwriting the  secondary master's mbr, it just appears that way when booting from grub2 menu. Disabling primary master in CMOS setup, has windows boot normally.

The 30_os-prober generates:

 ```
### BEGIN /etc/grub.d/30_os-prober ###
Found Windows 95/98/Me on /dev/sdb1
menuentry "Windows 95/98/Me (on /dev/sdb1)" {
	insmod fat
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2d27-07ee
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###
```

Which fails as above (dos compatibility mode), as does 40_custom, with all the permutations I've tried so far, like:

```
### BEGIN /etc/grub.d/40_custom ###
menuentry "Microsoft Windows" {
	insmod fat
	set root=(hd1,1)
	chainloader +1
	drivemap -s hd0 hd1
}
### END /etc/grub.d/40_custom ###
```

and have experimented with parttool and load_env/save_env, without success and am wondering if the problem is rootnoverify not being supported.

Would be grateful if anyone knows a configuration that works, as using CMOS/BIOS setup to boot windows is a pain.

---

### Post by drs305 on 2010-11-24
@ n.hinton

I have almost no experience with Windows and G2, but try something along these lines:

> 
menuentry “Microsoft Windows”  {
drivemap (hd0) (hd1)
drivemap (hd1) (hd0)
set root=(hd0)
chainloader  (hd1,1)+1
 }


---

### Post by n.hinton on 2010-11-24
Hi drs305,

Just ran that, double checked it was in grub.cfg (yes it was) but grub2 will not display that configuration as a menu item.

---

### Post by drs305 on 2010-11-24
n.hinton,

I think the problem was with the 'set root' command. I don't have Windows on the machine I'm using so I didn't try running it. The one below doesn't generate errors, but of course I cannot guarantee it will work either. You might play with the values in 'set root' and 'chainloader' if the one below doesn't work. 

> menuentry "Microsoft Windows" {
insmod part_msdos
insmod ntfs
drivemap (hd0) (hd1)
drivemap (hd1) (hd0)
set root='(hd0,msdos1)'
chainloader (hd1,1)+1
}


If you don't get any more responses, I suggest you open a new thread with rootnoverify and Windows as key words that might attract those with the knowledge to help.

---

### Post by n.hinton on 2010-11-24
Using set root='(hd0,msdos1)' boots Lucid (primary master), thanks though, will keep experimenting.

---

### Post by n.hinton on 2010-11-24
Sorry the above is not correct. Using set root='(hd0)' boots Lucid, set root='(hd0,msdos1)' or (hd1,msdos1) results in 'no such partition' message.

---

### Post by drs305 on 2010-11-24
Well, my last thought on the subject - get rid of the 'set root' line and substitute the  'search' line format and see if that works. As I said, I'm out of my league on Windows. Feel free to PM me with things that don't work or post here when you find a solution.

---

### Post by Jetro on 2010-11-25
Why is this so DAMN complicated compared to the old GRUB system? :|

---

### Post by n.hinton on 2010-12-04
> **drs305 said:**
> Well, my last thought on the subject - get rid of the 'set root' line and substitute the  'search' line format and see if that works. As I said, I'm out of my league on Windows. Feel free to PM me with things that don't work or post here when you find a solution.

[http://ubuntuforums.org/showpost.php?p=10198577&postcount=24](http://ubuntuforums.org/showpost.php?p=10198577&postcount=24)

---

### Post by not_the_geekiest on 2010-12-06
Can someone help me with this?

i currently see > Ubuntu, with Linux 2.6.35-23-generic-pae
Ubuntu, with Linux 2.6.35-23-generic-pae (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console *I forgot what number was here*)
Windows 7 (loader) (on /dev/sda1)
Windows 7 (loader) (on /dev/sda2)
Windows Vista (loader) (on /dev/sda3)
First of all, what is sda1-3? Which one is windows 7 recovery mode? How can I make it so that I just see this:
> Ubuntu
Ubuntu (recovery mode)
Windows 7
Windows 7 (recovery mode)
So I think that I understand that I should put > sudo chmod -x /etc/grub.d/20_memtest86+ in my command line in order not to see both memory tests. Is that correct?

After that I did not understand what I should write and, mainly, where I should write it.



[SIZE="1"]ps. If you could not tell from my post, I am a beginner, so please write what I should do with little programming jargon, or better yet, explain it to me.[/SIZE]

---

### Post by drs305 on 2010-12-06
Yes, if you run the 'chmod' command it will eliminate the memtest86+ entry.

If you would run the boot info script from the following link and then just attach the RESULTS.txt to a post I can take a look at it (you don't have to display it, just attach the file). We can change the titles if you are willing to edit some of the script files. The address for forum member *meierfra's* boot info script and how to run it are found here:
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by not_the_geekiest on 2010-12-06
Thank you drs305. I uploaded my txt file.

---

### Post by drs305 on 2010-12-06
not_the_geekiest,

Attached is a 40_custom file. Based on your desires, it's the easiest way to do what you want.
Change to the folder the file was saved to. Once there, run the command to rename the file to 40_custom and move it to the /etc/grub.d folder:
```
sudo mv 40_custom.txt /etc/grub.d/40_custom
```

Make it executable and owned by root:
```
sudo chmod +x /etc/grub.d/40_custom
sudo chown root: /etc/grub.d/40_custom

```
Notes on the file:
[LIST=a]
[*]You can change the title on any of the menuentry lines - change anything between the quotation marks.
[*]The way the linux menuentries are written, the custom menu will always use the latest kernel since the specific kernel version is not included. When 2.6.35-23-generic-pae comes out, it will automatically be used instead of 2.6.35-22-generic-pae, for instance.
[*]For the Windows entries, you will have to decide what each one does and rename the ones you want to keep and remove the ones you don't.
[*]These menu entries will initially appear at the bottom of your current menu. Once you are satisfied they work the way you want, disable the 10_linux and 30_os-prober scripts with the following command, as well as the memtest86+ script. Think of this command as your normal grub menu's 'on/off' switch. "chmod - ..." is off, "chmod + ..." is on.
[*]sudo chmod -x /etc/grub.d/10_linux /etc/grub.d/30_os-prober /etc/grub.d/20_memtest86+
[*]If you want to see all the options/kernels available, run the previous command with +x to make them executable again and then update grub (sudo update-grub). You can then inspect /boot/grub/grub.cfg and copy any new menuentry to your 40_custom file.
[*]Any time you make a change, you will have to update the grub.cfg menu to see the changes. Run:
```
sudo update-grub
```
[/LIST]

---

### Post by not_the_geekiest on 2010-12-07
okay, I used the command "# sudo chmod -x /etc/grub.d/10_linux /etc/grub.d/30_os-prober /etc/grub.d/20_memtest86+' and that added what I wanted to the end of the list but, how do I remove the old menu?

---

### Post by drs305 on 2010-12-07
> **not_the_geekiest said:**
> okay, I used the command "# sudo chmod -x /etc/grub.d/10_linux /etc/grub.d/30_os-prober /etc/grub.d/20_memtest86+' and that added what I wanted to the end of the list but, how do I remove the old menu?

I assume you didn't run the command starting with the **#** symbol. After you run "sudo chmod ..." you need to run "sudo update-grub" to make sure the menu is changed. The /boot/grub/grub.cfg file will still exist, but it's contents should include menu entries only from you 40_custom file.

You can preview what you will see for menu options when you boot by running the following command:
```

grep menuentry /boot/grub/grub.cfg
```

---

### Post by not_the_geekiest on 2010-12-07
Oops, sorry about that.

Thank you, everything works now. I just wanted to say that people like you are one of the main reasons that I decided to use Linux.

Also, in case you were wondering, sda1 is Windows 7, sda2 is the boot manager, and vista (sda3) is recovery mode.

---

### Post by jlh68 on 2010-12-12
I tried tip #6 to try to hide the vista loader.  It was unsuccessful as there was an error on line 171, and line 171 was not one that was changed.  I have attached part of my GRUB file for you to look at, my changes in red font.

Line 171:    menuentry "${LONGNAME} (on ${DEVICE})" {

I got a error on line 171 due to the { and the command expecting something else.  Again line 171 is original.

---

### Post by jlh68 on 2010-12-12
Here is the command output

> john@NightHawk:~$ gksu gedit +83 /etc/grub.d/30_os-prober &
[1] 3033
john@NightHawk:~$ sudo update-grub
[sudo] password for john: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-23-generic
Found initrd image: /boot/initrd.img-2.6.35-23-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /memtest86+.bin
/etc/grub.d/30_os-prober: 171: Syntax error: "(" unexpected (expecting "done")
john@NightHawk:~$ 


I also found some spaces in what I had entered, removed them and then updated grub, and this is the message returned.

---

### Post by drs305 on 2010-12-12
jlh68,

The problem is in the quotes in this line:
> if ["$LONGNAME"='Windows Vista (loader)**[COLOR="Red"]"[/COLOR]**] && ["${DEVICE}=**[COLOR="Red"]'[/COLOR]**/dev/sda1**[COLOR="Red"]"[/COLOR]**];then continue

The quote types don't match defining [COLOR="Red"][SIZE="4"]'[/SIZE][/COLOR]Windows Vista (loader)[COLOR="Red"][SIZE="4"]"[/SIZE][/COLOR] and then also in /dev/sda1. The line should be:
> 
# Added to remove Windows Recovery
if [ "$LONGNAME" = "Windows Vista (loader)" ] && [ "${DEVICE}" = "/dev/sda1" ] ; then
continue
fi
# End Added



Or you can use double quotes, as long as you use the same on both ends. 

It's easier just to copy.  ;-)

---

### Post by jlh68 on 2010-12-12
Made corrections, saved and updated then got this error, which is the line I am working with.  I had seen one of the quote symbols was incorrect, but not the second one.  Thanks/ 

> john@NightHawk:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-23-generic
Found initrd image: /boot/initrd.img-2.6.35-23-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /memtest86+.bin
/etc/grub.d/30_os-prober: 160: Syntax error: "then" unexpected (expecting "done")

---

### Post by jlh68 on 2010-12-12
Here is new file (actually just the lines we are working with.

> # Added to remove Windows Recovery
if["$LONGNAME"="Windows Vista (loader)"]&&["${DEVICE}"="/dev/sda1"];then continue
fi
#End Added

---

### Post by jlh68 on 2010-12-12
OK **drs305** I cut and pasted your line from your last post and then saved, then updated grub, restarted and now it is working.

THANKS.  Thanks for working with me on this.

---

### Post by Imam86 on 2010-12-14
> **Antonello Amici said:**
> for capitalize the first letter of codename

```
codename=`lsb_release -cs | sed "s/^./\u&/"`
```;)


It's not working..    
         
:(

---

### Post by Imam86 on 2010-12-14
> **Antonello Amici said:**
> for capitalize the first letter of codename

```
codename=`lsb_release -cs | sed "s/^./\u&/"`
```;)


It's not working..    
         
:(

---

### Post by drs305 on 2010-12-14
> **Imam86 said:**
> It's not working..    
         
:(
Imam86,

Welcome to the Ubuntu forums.  :-)

I assume you got that command from *Antonello Amici's* Post #41.  When I run the command on my system, without the variable name and quotes:
```
lsb_release -cs | sed "s/^./\u&/"
```
I get: *Maverick* so the command you pasted is working for me. Does it work for you in a terminal?

If you will attach your /etc/grub.d/10_linux file (or the file you are trying to modify) we can see where the problem is.

---

### Post by Mike_tn on 2011-01-10
how to edit Grub menu for Kubuntu and Ubuntu each on their own partition?

---

### Post by drs305 on 2011-01-10
> **Mike_tn said:**
> how to edit Grub menu for Kubuntu and Ubuntu each on their own partition?

I'm not sure what you are asking. The one in the running OS would be located in the /etc/grub.d/10_linux file. The one in the non-running partition would be 'controlled' by the settings in /etc/grub.d/30_os-prober.

I'll take this opportunity to refer users to my latest Grub 2 guide on Grub Customizer. It's a GUI tool that can do just about everything that can be found in this guide, but in a much easier manner. For those awaiting a more functional version of StartUp-Manager for Grub2, this one will do it and more.
[_HOWTO: Grub Customizer_]("http://ubuntuforums.org/showthread.php?p=10340183#post10340183")

---

### Post by Mike_tn on 2011-01-11
> **drs305 said:**
> I'm not sure what you are asking. The one in the running OS would be located in the /etc/grub.d/10_linux file. The one in the non-running partition would be 'controlled' by the settings in /etc/grub.d/30_os-prober.[]("http://ubuntuforums.org/showthread.php?p=10340183#post10340183")

I meant if I install using 3 partitions, one for each, two Grub2 using versions of Ubuntu, plus a Windows OS, then what will happen? From what I read on the forums, only the Ubuntu version installed second and the Windows will appear on the Grub menu. I'd like all three in the Grub menu at boot time. I havn't tried this yet but I might. Or I might install Debian Squeeze stable with Grub2 (due to be available soon) but alongside Ubuntu Maverick and Windows.  How to get boot menu showing all of 3 them? Perhaps you suggest I should just use your new GUI or wait on the new Startup Manager. thanks

---

### Post by drs305 on 2011-01-11
> **Mike_tn said:**
> I meant if I install using 3 partitions, one for each, two Grub2 using versions of Ubuntu, plus a Windows OS, then what will happen? From what I read on the forums, only the Ubuntu version installed second and the Windows will appear on the Grub menu. I'd like all three in the Grub menu at boot time. I havn't tried this yet but I might. Or I might install Debian Squeeze stable with Grub2 (due to be available soon) but alongside Ubuntu Maverick and Windows. 

How to get boot menu showing all of 3 them?  

Grub2 should find all your OS's. It uses os-prober to search all your mounted partitions for other systems. It looks for the Windows boot files and linux grub.cfg, grub.conf and menu.lst files. So it should locate each of your other systems and automatically add them to your G2 menu. 

If for some reason it doesn't you can manually add the necessary menuentries to the 40_custom menu. If some OS's are missing, post a copy of RESULTS.txt and we can probably build the menu entries for you. 

> 
Perhaps you suggest I should just use your new GUI or wait on the new Startup Manager. thanks

It's not *my* new GUI, I just wrote a short guide on how to use it. And after experimenting with it for the past day I am quite happy with Grub Customizer's capabilities and can recommend it. 

It doesn't find the OS's itself, it just tweaks the data found by Grub2 to present it in a manner desired by the user.

---

### Post by Mike_tn on 2011-01-11
thanks!

---

### Post by Sylslay on 2011-01-12
Nice "How to"
Useful for me.

---

### Post by Gandalf1962 on 2011-01-14
Ok, I have a problem I have racked my brain over for about 2 weeks. I have 5 distros of linux along with windows vista and my xp recovery partition with Grub2 and Burg. I am trying to set the gfxpayload to 1280x1024 on all 5 of the linux distros. I have tried changing each of the grub.cfg files manually and updating but still doesn't work only for the distro that has grub2 and burg installed. I can manually edit the boot line each time I boot up and it works fine. Just can't figure out where to go to have it applied across all distros each time I run update-burg. Can anyone help? I will attach my burg.cfg and 11_os-prober_proxy file. Any help would be greatly appreciated.

---

### Post by drs305 on 2011-01-14
> **Gandalf1962 said:**
> Ok, I have a problem I have racked my brain over for about 2 weeks. I have 5 distros of linux along with windows vista and my xp recovery partition with Grub2 and Burg. I am trying to set the gfxpayload to 1280x1024 on all 5 of the linux distros. I have tried changing each of the grub.cfg files manually and updating but still doesn't work only for the distro that has grub2 and burg installed. I can manually edit the boot line each time I boot up and it works fine. Just can't figure out where to go to have it applied across all distros each time I run update-burg. Can anyone help? I will attach my burg.cfg and 11_os-prober_proxy file. Any help would be greatly appreciated.

Gandalf1962,

Welcome to the Ubuntu forums.

First some disclaimers, or if you prefer, some assumptions. I don't use BURG. From the files you mention, I also assume you have tried or are using Grub Customizer (unless BURG works the same way); even though I wrote a [_[U]HOWTO_[/U]]("http://ubuntuforums.org/showthread.php?p=10340183#post10340183") on using Grub Customizer, I haven't explored it's file management to any great extent. Also I'll have to trust you as far as the 'gfxmode' setting working for all the distros you want to use it in.

You are using 11xxx script. I've tested with 30_osprober. I believe Grub Customizer moves that file into the Proxy folder and renames it os-prober. I don't know if your changes need to be made to os-prober, but that's my assumption. The modification worked for me by making the change to 30_os-prober - you'll have to figure out which script to change.

Anyway..... Since you want it to apply for all linux entries, I think only one line needs to be added.

In 30_os-prober's "linux)" section, I added the following just below approximately line 209:
> 
        cat << EOF
menuentry "${LLABEL} (on ${DEVICE})" {
        **set gfxmode=1280x1024**
EOF


This is in the "linux)"  section so it will only be placed in Linux entries found by os-prober.

Save the file and update-grub (or burg, as appropriate).

---

### Post by Gandalf1962 on 2011-01-14
> **drs305 said:**
> Gandalf1962,


In 30_os-prober's "linux)" section, I added the following just below approximately line 209:


This is in the "linux)"  section so it will only be placed in Linux entries found by os-prober.

Save the file and update-grub (or burg, as appropriate).

You were right on the money. It worked like a champ. THANKS for the quick response.
Maybe know I can grow all the hair I pulled out back while trying to get this to work.

Thanks again. Keep up the good!!!!!!!!!!! 

:D

---

### Post by Gandalf1962 on 2011-01-14
:(

---

### Post by Gandalf1962 on 2011-01-14
:(

---

### Post by Gandalf1962 on 2011-01-14
:(

---

### Post by moonlight_sonata on 2011-02-20
hello. i want to ask something.
i have a plan to remaster ubuntu 10.04 for my lab (educational).
everything goes smoth until this problrm.

when first booting on live-cd, first will going to GRUB 2. like this

                                           GNU GRUB Version 1.97, Ubuntu

Live
xforcevesa
memtest

that grub menu.
how to change GRUB Title (GNU GRUB Version 1.97, Ubuntu) become my Distro name?
i saw GnackTrack, they can change GNU GRUB Version become GnackTrack R3.

thanks before . it's very help me.

---

### Post by drs305 on 2011-02-21
> **moonlight_sonata said:**
> 
how to change GRUB Title (GNU GRUB Version 1.97, Ubuntu) become my Distro name?
i saw GnackTrack, they can change GNU GRUB Version become GnackTrack R3.

I have found several files in the Grub2 libraries that define the title during the running of scripts, but I haven't been able to find the one that actually changes the title. It's possible that the main title is not editable via any normal means by the user. 

You could ask the developers directly, who hang out on the IRC channel at #grub. If you aren't familiar with it, here is a link to IRC and a second I wrote on xChat, which can help you get connected to the channels if you don't already have another client.
[_https://help.ubuntu.com/community/InternetRelayChat_]("https://help.ubuntu.com/community/InternetRelayChat")

[_https://help.ubuntu.com/community/XChatHowto_]("https://help.ubuntu.com/community/XChatHowto")

If you find an answer please let us know.

---

### Post by tetobear on 2011-04-08
Hello dsr305,
congrat for the great information about grub2

I have two questions...

I'm trying out ubuntu studio 11.04 with grub 1.99
1. Does Grub Customizer work with grub 1.99?
2. the background is set on black and it show black!I set a pic for background and I can see the pic just around the border... ( i used the code u post on #4)...

thank you

---

### Post by drs305 on 2011-04-09
> **tetobear said:**
> I'm trying out ubuntu studio 11.04 with grub 1.99
1. Does Grub Customizer work with grub 1.99?

Yes. I haven't tested all the changes, such as the submenu for extra linux kernels, but for the most part it does. The creator is staying on top of things so anything that might not work yet will probably be fixed in the near future.

> 
2. the background is set on black and it show black!I set a pic for background and I can see the pic just around the border... ( i used the code u post on #4)...
thank you
Since you are using Grub 1.99, backgrounds should be a bit easier. I wrote a guide about a new feature with Grub 1.99 and backgrounds. Here is the link:
[Grub Background - Simple Drag & Drop1718521]("http://ubuntuforums.org/showthread.php?t=1718521")
If /black isn't working for you as a transparency, make sure it is an RGB indexed image. You could also try one of the default images by downloading the 'grub2-splashimages' package and using one of the ones placed in /usr/share/images/grub just to see if you might be having an image formatting problem.

---

### Post by tetobear on 2011-04-11
Thank you very much for your quick answers!

Yes I am using a custom pic I just use gimp to save it at the grub resolution that I set.
Well today the pic showed up after the dayly updated of the ubuntu studio beta I guess.

> 
If /black isn't working for you as a transparency, make sure it is an RGB indexed image. You could also try one of the default images by downloading the 'grub2-splashimages' package and using one of the ones placed in /usr/share/images/grub just to see if you might be having an image formatting problem.
I didnt know about this special issue so thank you so much for the precious info!
Now everything is working!
Excellent job!

---

### Post by ranch hand on 2011-04-11
Run one of the grub splash images through gimp with the one you want to use.  Make sure that all the image options are the same and your custom one will have no problem.  Gimp can handle it easily.

---

### Post by drs305 on 2011-04-12
> **ranch hand said:**
> Make sure that all the image options are the same and your custom one will have no problem.  Gimp can handle it easily.

And for the record, the grub2-splashimages provides images with the following properties:
Type: .tga 
Size: 640x480
Resolution: 72x72 ppi
Color: RGB

---

### Post by arthurdent22 on 2011-08-06
There is an error in the instructions for "11. HIDING THE MENU ON MULTI-OS SYSTEMS".

Method 2. the line to change in /etc/grub.d/30_os-prober is wrongly shown as
if [ "x${GRUB_DISABLE_OS_PROBER}" = "xtrue" ]; then  

The actual line to change is this one
if [ "x${found_other_os}" = "x" ] ; then

---

### Post by drs305 on 2011-08-06
> **arthurdent22 said:**
> There is an error in the instructions ...

I readily admit I'm not a coder. As I read it though, I edit  
> if [ "x${GRUB_DISABLE_OS_PROBER}" = "xtrue" ]; then 
which is the first conditional run in the script. It runs the "adjust timeout" function which will set the timeout to 0 and then exit the script.

You advise editing the 'adjust_timeout' function itself, but I think since the line I alter is the first conditional run it won't make a difference.

I think I do see a 'hole' in that if "GRUB_HIDDEN_TIMEOUT" happened to be commented out the menu would still display under certain conditions, but that would be the case in either of our modifications. And commenting that line is an undocumented hack to always display the menu...

Again, I don't write scripts often so if what I've written is incorrect (as opposed to inelegant) please feel free to correct me.

---

### Post by Ubunfoo on 2011-08-13
Hey bros, 

I'm still learning how to read these code and script pages, and although being able to follow your guide quite easily (Thanks!), I feel I have made a boo-boo of uncertain proportions, haha.  I am following your guide but I actually use BURG so I am editing the /etc/burg.d/ files instead of the GRUB files.  I made two changes to the OS Probe file.  The first was removing the partition tag from the menu item, which is awesome and it worked great.  I did this for three OS's: Kubuntu 11.04, Windows 7, and Backtrack5, and the burg emulator proved there were no problems with that edit.  :D  Second, I decided I'd like to hide the windows recovery menu item.  I added the line you specified, and edited it for  me:

```
#Added to remove Windows Recovery
if ["$LONGNAME"="Windows 7 (loader)"]&&["${DEVICE}"="/dev/sda1"]; then
continue
fi
```Then I saved the file, ran: sudo update-burg and then sudo burg-emu -D.

Both windows 7 menu items and both backtrack5 items are gone.  Both Kubuntu items (regular and recovery) are present....I undid ALL the changes I made to the OS prober, saved it, updated burg, and emulated again, and still, only the two kubuntu list items remain.  I'm doing all of this in kubuntu, and I'm freakin out I just F'd up bigtime somehow, but it doesn't make sense that when I undo all of the changes both items are still gone.  

If anyone can lend me some help with this, I would really appreciate it! Thanks!

Ryan

---

### Post by drs305 on 2011-08-13
> **Ubunfoo said:**
> If anyone can lend me some help with this, I would really appreciate it! Thanks!

Ryan

Ryan, Sorry the second tweak didn't work, but don't worry. There isn't anything that tweaking os-prober can do to your actual system - only to the menu. 

Did you happen to make or have a backup of your original grub.cfg file? If so, you can cut/paste the menuentries for the missing systems into /etc/grub.d/40_custom so you have them available after your update grub.

If you post your /etc/grub.d/30_os-prober script (or BURG equivalent) and run the boot info script and post the contents of RESULTS.txt we can see what's going on and get things back to normal. I'm not an expert on BURG and don't know anything about grub-emu, but if I can't figure it out someone else may happen by.
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by Ubunfoo on 2011-08-14
drs305,

Thanks for getting back to me about this!  I'm glad to hear I didn't finally a dig a hole I can't get out of, haha.

As for the grub.cfg file, I haven't touched it, so it should be ok still.  Cutting/pasting menu entries into 40_custom, Im assuming that will work for burg.cfg instead of grub.cfg?  I don't really know, but it seems logical, so I guess I'll be trying that.  Thanks!

My /etc/burg.d/30_os prober file is as follows (this should be how it looked before I made any changes, although I still cannot see Windows 7 or Backtrack. I tried to attach it so you'd have line #'s, but it wont upload, so copying/pasting it might be easiest):

```
#! /bin/sh -e

# grub-mkconfig helper script.
# Copyright (C) 2006,2007,2008,2009  Free Software Foundation, Inc.
#
# GRUB is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# GRUB is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with GRUB.  If not, see <http://www.gnu.org/licenses/>.

prefix=/usr
exec_prefix=${prefix}
libdir=${exec_prefix}/lib

. ${libdir}/burg/burg-mkconfig_lib

if [ "x${GRUB_DISABLE_OS_PROBER}" = "xtrue" ]; then
  exit 0
fi

if [ -z "`which os-prober 2> /dev/null`" -o -z "`which linux-boot-prober 2> /dev/null`" ] ; then
  # missing os-prober and/or linux-boot-prober
  exit 0
fi

OSPROBED="`os-prober | tr ' ' '^' | paste -s -d ' '`"
if [ -z "${OSPROBED}" ] ; then
  # empty os-prober output, nothing doing
  exit 0
fi

osx_entry() {
        cat << EOF
menuentry "${LONGNAME} (${2}-bit) (on ${DEVICE})" --class ${OSLABEL} --class os ${AUTH_NORMAL}{
EOF
    save_default_entry | sed -e "s/^/\t/"
    prepare_grub_to_access_device ${DEVICE} | sed -e "s/^/\t/"
    cat << EOF
        insmod ${GRUB_VIDEO_BACKEND}
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ \$do_resume == 0 ]; then
           xnu_uuid ${OSXUUID} uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           $1 /mach_kernel boot-uuid=\${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
EOF
}

export AUTH_NORMAL AUTH_RESCUE

for OS in ${OSPROBED} ; do
  DEVICE="`echo ${OS} | cut -d ':' -f 1`"
  LONGNAME="`echo ${OS} | cut -d ':' -f 2 | tr '^' ' '`"
  LABEL="`echo ${OS} | cut -d ':' -f 3 | tr '^' ' '`"
  BOOT="`echo ${OS} | cut -d ':' -f 4`"

  OSLABEL="$(echo ${LABEL} | tr '[A-Z]' '[a-z]' | cut -d' ' -f1 | sed 's,[0-9]*$,,')"
  if [ -z "${OSLABEL}" ] ; then
    OSLABEL="unknown";
  fi
  case $OSLABEL in
    mandriva*)
      OSLABEL=mandrake
    ;;
  esac
  get_auth_option ${OSLABEL}

  if [ -z "${LONGNAME}" ] ; then
    LONGNAME="${LABEL}"
  fi

  s=`echo :${GRUB_TITLE_OVERRIDE}: | sed "s,.*:${DEVICE}=\([^:]*\):.*,\1,"`
  if test "x$s" != "x:${GRUB_TITLE_OVERRIDE}:" ; then
    LONGNAME="$s"
  fi

  s=`echo :${GRUB_CLASS_OVERRIDE}: | sed "s,.*:${DEVICE}=\([^:]*\):.*,\1,"`
  if test "x$s" != "x:${GRUB_CLASS_OVERRIDE}:" ; then
    OSLABEL="$s"
  fi

  echo "Found ${LONGNAME} on ${DEVICE}" >&2

  case ${BOOT} in
    chain)

      cat << EOF
menuentry "${LONGNAME} (on ${DEVICE})" --class ${OSLABEL} --class os ${AUTH_NORMAL}{
EOF
      save_default_entry | sed -e "s/^/\t/"
      prepare_grub_to_access_device ${DEVICE} | sed -e "s/^/\t/"

      case ${LONGNAME} in
    Windows\ Vista*|Windows\ 7*)
    ;;
    *)
      cat << EOF
    drivemap -s (hd0) \${root}
EOF
    ;;
      esac

      cat <<EOF
    chainloader +1
}
EOF
    ;;
    linux)
      LINUXPROBED="`linux-boot-prober ${DEVICE} 2> /dev/null | tr ' ' '^' | paste -s -d ' '`"
      prepare_boot_cache=

      for LINUX in ${LINUXPROBED} ; do
        LROOT="`echo ${LINUX} | cut -d ':' -f 1`"
        LBOOT="`echo ${LINUX} | cut -d ':' -f 2`"
        LLABEL="`echo ${LINUX} | cut -d ':' -f 3 | tr '^' ' '`"
        LKERNEL="`echo ${LINUX} | cut -d ':' -f 4`"
        LINITRD="`echo ${LINUX} | cut -d ':' -f 5`"
        LPARAMS="`echo ${LINUX} | cut -d ':' -f 6- | tr '^' ' '`"

        if [ -z "${LLABEL}" ] ; then
          LLABEL="${LONGNAME}"
        fi

    if [ "${LROOT}" != "${LBOOT}" ]; then
      LKERNEL="${LKERNEL#/boot}"
      LINITRD="${LINITRD#/boot}"
    fi

        cat << EOF
menuentry "${LLABEL} (on ${DEVICE})" --class ${OSLABEL} --class os --group group_${DEVICE} ${AUTH_NORMAL}{
EOF
    save_default_entry | sed -e "s/^/\t/"
    if [ -z "${prepare_boot_cache}" ]; then
      prepare_boot_cache="$(prepare_grub_to_access_device ${LBOOT} | sed -e "s/^/\t/")"
    fi
    printf '%s\n' "${prepare_boot_cache}"
    cat <<  EOF
    linux${GRUB_LINUX16} ${LKERNEL} ${LPARAMS}
EOF
        if [ -n "${LINITRD}" ] ; then
          cat << EOF
    initrd${GRUB_LINUX16} ${LINITRD}
EOF
        fi
        cat << EOF
}
EOF
      done
    ;;
    macosx)
      OSXUUID="`burg-probe --target=fs_uuid --device ${DEVICE} 2> /dev/null`"
      osx_entry xnu_kernel 32
      osx_entry xnu_kernel64 64
    ;;
    hurd)
      cat << EOF
menuentry "${LONGNAME} (on ${DEVICE})" --class ${OSLABEL} --class os ${AUTH_NORMAL}{
EOF
      save_default_entry | sed -e "s/^/\t/"
      prepare_grub_to_access_device ${DEVICE} | sed -e "s/^/\t/"
      grub_device="`${grub_probe} --device ${DEVICE} --target=drive`"
      mach_device="`echo "${grub_device}" | tr -d '()' | tr , s`"
      grub_fs="`${grub_probe} --device ${DEVICE} --target=fs`"
      case "${grub_fs}" in
    *fs)    hurd_fs="${grub_fs}" ;;
    *)    hurd_fs="${grub_fs}fs" ;;
      esac
      cat << EOF
    multiboot /boot/gnumach.gz root=device:${mach_device}
    module /hurd/${hurd_fs}.static ${hurd_fs} --readonly \\
            --multiboot-command-line='\${kernel-command-line}' \\
            --host-priv-port='\${host-port}' \\
            --device-master-port='\${device-port}' \\
            --exec-server-task='\${exec-task}' -T typed '\${root}' \\
            '\$(task-create)' '\$(task-resume)'
    module /lib/ld.so.1 exec /hurd/exec '\$(exec-task=task-create)'
}
EOF
    ;;
    *)
      echo "  ${LONGNAME} is not yet supported by burg-mkconfig." >&2
    ;;
  esac
done

```You should be able to fi nd Kubuntu, Backtrack and their recovery modes, as well as Windows 7 and the recovery partition if I have read it all correctly (no guarantees there...).

What might also be helpful, is a list I kept of every change I made to it as I was editing along with the guide.  My menu items disappeared after I edited in the last item, and wouldn't reappear after reverting all my changes. (again, these aren't in the copy above anymore): 


[LIST]
[*]**line 130 - After {LONGNAME} deleted (on ${DEVICE})**
[*]**line 172 - After {LLABEL} deleted     (on ${DEVICE})**
[*]**line 42 - After (${2}-bit) deleted     (on ${DEVICE})**
[*][B]line 114 - added:
    #Added to remove Windows Recovery
if ["$LONGNAME"="Windows 7 (loader)"]&&["${DEVICE}"="/dev/sda1"]; then
continue
fi[/B]
[/LIST]
The contents of RESULTS.txt are as follows:
```

                  
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub Legacy (v0.97) is installed in the MBR of /dev/sda and looks on the 
    same drive in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub Legacy
    Boot sector info:   Grub Legacy (v0.97) is installed in the boot sector 
                       of sda6 and looks at sector 435988224 of the same hard 
                       drive for the stage2 file.  A stage2 file is at this 
                       location on /dev/sda.  Stage2 looks on partition #6 
                       for /boot/grub/menu.lst.
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.cfg 
                       /boot/burg/burg.cfg /etc/fstab /boot/grub/core.img 
                       /boot/burg/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  BackTrack 5 - Code Name 
                       Revolution 32 bit
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda9: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda4 has 
                       30722047 sectors, but according to the info from 
                       fdisk, it has 30943919 sectors.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       411,647       409,600   7 NTFS / exFAT / HPFS
/dev/sda2             411,648   435,448,541   435,036,894   7 NTFS / exFAT / HPFS
/dev/sda3         435,449,854   594,198,527   158,748,674   f W95 Extended (LBA)
/dev/sda5         533,391,360   594,198,527    60,807,168   7 NTFS / exFAT / HPFS
/dev/sda6         435,449,856   484,766,567    49,316,712  83 Linux
/dev/sda7         529,201,152   533,389,311     4,188,160  82 Linux swap / Solaris
/dev/sda8         484,767,744   527,259,647    42,491,904  83 Linux
/dev/sda9         527,261,696   529,197,055     1,935,360  82 Linux swap / Solaris
/dev/sda4         594,198,528   625,142,447    30,943,920  12 Compaq diagnostics


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        CE72CBC572CBB10F                       ntfs       
/dev/sda2        8C24CA4E24CA3B4A                       ntfs       
/dev/sda4        A2D0FC85D0FC60C9                       ntfs       LENOVO_PART
/dev/sda5        86563F9A563F8A47                       ntfs       LENOVO
/dev/sda6        bfc79931-2ce4-449d-8a70-3e98451dfac3   ext4       
/dev/sda7        743aed1b-6694-4e50-a185-4947370a1447   swap       
/dev/sda8        27d965de-f62c-4689-a65b-7d8b3fb96f69   ext4       
/dev/sda9        557fe2bc-bc85-4dd8-b7c6-63bad8e4bbd8   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda6/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
# menu.lst - See: grub( 8 ), info grub, update-grub(Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub Legacy (v0.97) is installed in the MBR of /dev/sda and looks on the 
    same drive in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub Legacy
    Boot sector info:   Grub Legacy (v0.97) is installed in the boot sector 
                       of sda6 and looks at sector 435988224 of the same hard 
                       drive for the stage2 file.  A stage2 file is at this 
                       location on /dev/sda.  Stage2 looks on partition #6 
                       for /boot/grub/menu.lst.
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.cfg 
                       /boot/burg/burg.cfg /etc/fstab /boot/grub/core.img 
                       /boot/burg/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  BackTrack 5 - Code Name 
                       Revolution 32 bit
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda9: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda4 has 
                       30722047 sectors, but according to the info from 
                       fdisk, it has 30943919 sectors.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       411,647       409,600   7 NTFS / exFAT / HPFS
/dev/sda2             411,648   435,448,541   435,036,894   7 NTFS / exFAT / HPFS
/dev/sda3         435,449,854   594,198,527   158,748,674   f W95 Extended (LBA)
/dev/sda5         533,391,360   594,198,527    60,807,168   7 NTFS / exFAT / HPFS
/dev/sda6         435,449,856   484,766,567    49,316,712  83 Linux
/dev/sda7         529,201,152   533,389,311     4,188,160  82 Linux swap / Solaris
/dev/sda8         484,767,744   527,259,647    42,491,904  83 Linux
/dev/sda9         527,261,696   529,197,055     1,935,360  82 Linux swap / Solaris
/dev/sda4         594,198,528   625,142,447    30,943,920  12 Compaq diagnostics


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        CE72CBC572CBB10F                       ntfs       
/dev/sda2        8C24CA4E24CA3B4A                       ntfs       
/dev/sda4        A2D0FC85D0FC60C9                       ntfs       LENOVO_PART
/dev/sda5        86563F9A563F8A47                       ntfs       LENOVO
/dev/sda6        bfc79931-2ce4-449d-8a70-3e98451dfac3   ext4       
/dev/sda7        743aed1b-6694-4e50-a185-4947370a1447   swap       
/dev/sda8        27d965de-f62c-4689-a65b-7d8b3fb96f69   ext4       
/dev/sda9        557fe2bc-bc85-4dd8-b7c6-63bad8e4bbd8   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda6/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
# menu.lst - See: grub( 8 ), info grub, update-grub( 8 )
#            grub-install( 8 ), grub-floppy( 8 ),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=bfc79931-2ce4-449d-8a70-3e98451dfac3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=bfc79931-2ce4-449d-8a70-3e98451dfac3

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 11.04, kernel 2.6.38-10-generic
uuid        bfc79931-2ce4-449d-8a70-3e98451dfac3
kernel        /boot/vmlinuz-2.6.38-10-generic root=UUID=bfc79931-2ce4-449d-8a70-3e98451dfac3 ro quiet splash 
initrd        /boot/initrd.img-2.6.38-10-generic
quiet

title        Ubuntu 11.04, kernel 2.6.38-10-generic (recovery mode)
uuid        bfc79931-2ce4-449d-8a70-3e98451dfac3
kernel        /boot/vmlinuz-2.6.38-10-generic root=UUID=bfc79931-2ce4-449d-8a70-3e98451dfac3 ro  single
initrd        /boot/initrd.img-2.6.38-10-generic

title        Chainload into GRUB 2
root        bfc79931-2ce4-449d-8a70-3e98451dfac3
kernel        /boot/grub/core.img

title        Ubuntu 11.04, memtest86+
uuid        bfc79931-2ce4-449d-8a70-3e98451dfac3
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
--------------------------------------------------------------------------------

=========================== sda6/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root bfc79931-2ce4-449d-8a70-3e98451dfac3
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root bfc79931-2ce4-449d-8a70-3e98451dfac3
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 0,71,115; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root bfc79931-2ce4-449d-8a70-3e98451dfac3
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=bfc79931-2ce4-449d-8a70-3e98451dfac3 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root bfc79931-2ce4-449d-8a70-3e98451dfac3
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=bfc79931-2ce4-449d-8a70-3e98451dfac3 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root bfc79931-2ce4-449d-8a70-3e98451dfac3
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root bfc79931-2ce4-449d-8a70-3e98451dfac3
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root CE72CBC572CBB10F
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda4)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos4)'
    search --no-floppy --fs-uuid --set=root A2D0FC85D0FC60C9
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=========================== sda6/boot/burg/burg.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/burg-mkconfig using templates
# from /etc/burg.d and settings from /etc/default/burg
#

### BEGIN /etc/burg.d/00_header ###
set theme_name=burg
if [ -s $prefix/burgenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}
set gfxmode=1366x768
function select_menu {
  if menu_popup -t template_popup theme_menu ; then
    free_config template_popup template_subitem menu class screen
    load_config ${prefix}/themes/${theme_name}/theme ${prefix}/themes/custom/theme_${theme_name}
    save_env theme_name
    menu_refresh
  fi
}
function toggle_fold {
  if test -z $theme_fold ; then
    set theme_fold=1
  else
    set theme_fold=
  fi
  save_env theme_fold
  menu_refresh
}
function select_resolution {
  if menu_popup -t template_popup resolution_menu ; then
    menu_reload_mode
  fi
}
if test -f ${prefix}/themes/${theme_name}/theme ; then
  insmod coreui
  menu_region.text
  load_string '+theme_menu { -dark_shine { command="set theme_name=dark_shine" }}'
  load_string '+theme_menu { -minimal { command="set theme_name=minimal" }}'
  load_string '+theme_menu { -minimaltext { command="set theme_name=minimaltext" }}'
  load_string '+theme_menu { -vitruvio { command="set theme_name=vitruvio" }}'
  load_config ${prefix}/themes/conf.d/10_hotkey
  load_config ${prefix}/themes/${theme_name}/theme ${prefix}/themes/custom/theme_${theme_name}
  insmod vbe
  insmod png
  insmod jpeg
  set gfxfont="Unifont Regular 16"
  menu_region.gfx
  vmenu resolution_menu
  controller.ext
fi
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set bfc79931-2ce4-449d-8a70-3e98451dfac3
set locale_dir=($root)/boot/burg/locale
set lang=en
insmod gettext
set timeout=15
### END /etc/burg.d/00_header ###

### BEGIN /etc/burg.d/10_linux ###
menuentry 'Ubuntu GNU/Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os --group group_main {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set bfc79931-2ce4-449d-8a70-3e98451dfac3
    echo    'Loading Linux 2.6.38-10-generic ...'
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=bfc79931-2ce4-449d-8a70-3e98451dfac3 ro  quiet splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu GNU/Linux 2.6.38-10-generic (recovery mode)' --class  ubuntu --class gnu-linux --class gnu --class os --group group_main {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set bfc79931-2ce4-449d-8a70-3e98451dfac3
    echo    'Loading Linux 2.6.38-10-generic ...'
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=bfc79931-2ce4-449d-8a70-3e98451dfac3 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-10-generic
}
### END /etc/burg.d/10_linux ###

### BEGIN /etc/burg.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/burg.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=bfc79931-2ce4-449d-8a70-3e98451dfac3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=743aed1b-6694-4e50-a185-4947370a1447 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 219.984889984 = 236.206977024  boot/burg/burg.cfg                             1
 211.779014587 = 227.395985408  boot/burg/core.img                             1
 207.696395874 = 223.012306944  boot/grub/core.img                             1
 211.851543427 = 227.473862656  boot/grub/grub.cfg                             1
 228.307144165 = 245.142929408  boot/grub/menu.lst                             1
 207.895496368 = 223.226089472  boot/grub/stage2                               1
 228.662109375 = 245.524070400  boot/initrd.img-2.6.38-10-generic              2
 228.377265930 = 245.218222080  boot/vmlinuz-2.6.38-10-generic                 2
 228.662109375 = 245.524070400  initrd.img                                     2
 228.662109375 = 245.524070400  initrd.img.old                                 2
 228.377265930 = 245.218222080  vmlinuz                                        2
 228.377265930 = 245.218222080  vmlinuz.old                                    2

=========================== sda8/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0, 8 )'
search --no-floppy --fs-uuid --set 27d965de-f62c-4689-a65b-7d8b3fb96f69
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1024x768
  set gfxpayload=keep
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0, 8 )'
search --no-floppy --fs-uuid --set 27d965de-f62c-4689-a65b-7d8b3fb96f69
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.38' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0, 8 )'
    search --no-floppy --fs-uuid --set 27d965de-f62c-4689-a65b-7d8b3fb96f69
    linux    /boot/vmlinuz-2.6.38 root=UUID=27d965de-f62c-4689-a65b-7d8b3fb96f69 ro   text splash nomodeset vga=791
    initrd    /boot/initrd.img-2.6.38
}
menuentry 'Ubuntu, with Linux 2.6.38 (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0, 8 )'
    search --no-floppy --fs-uuid --set 27d965de-f62c-4689-a65b-7d8b3fb96f69
    echo    'Loading Linux 2.6.38 ...'
    linux    /boot/vmlinuz-2.6.38 root=UUID=27d965de-f62c-4689-a65b-7d8b3fb96f69 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0, 8 )'
    search --no-floppy --fs-uuid --set 27d965de-f62c-4689-a65b-7d8b3fb96f69
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0, 8 )'
    search --no-floppy --fs-uuid --set 27d965de-f62c-4689-a65b-7d8b3fb96f69
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set CE72CBC572CBB10F
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda4)" {
    insmod ntfs
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set A2D0FC85D0FC60C9
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set bfc79931-2ce4-449d-8a70-3e98451dfac3
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=bfc79931-2ce4-449d-8a70-3e98451dfac3 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set bfc79931-2ce4-449d-8a70-3e98451dfac3
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=bfc79931-2ce4-449d-8a70-3e98451dfac3 ro single
    initrd /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda8/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=27d965de-f62c-4689-a65b-7d8b3fb96f69 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=557fe2bc-bc85-4dd8-b7c6-63bad8e4bbd8 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda8: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 241.414634705 = 259.216990208  boot/grub/core.img                             1
 241.930671692 = 259.771080704  boot/grub/grub.cfg                             1
 231.317634583 = 248.375418880  boot/initrdf.img-2.6.38                        1
 233.213188171 = 250.410754048  boot/initrd.img-2.6.38                         2
 231.347160339 = 248.407121920  boot/initrds.img-2.6.38                        1
 241.914287567 = 259.753488384  boot/vmlinuz-2.6.38                            1
 233.213188171 = 250.410754048  initrd.img                                     2
 241.914287567 = 259.753488384  vmlinuz                                        1

========= Devices which don't seem to have a corresponding hard drive: =========

sdb 8 )
#            grub-install( 8 ), grub-floppy( 8 ),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=bfc79931-2ce4-449d-8a70-3e98451dfac3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=bfc79931-2ce4-449d-8a70-3e98451dfac3

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 11.04, kernel 2.6.38-10-generic
uuid        bfc79931-2ce4-449d-8a70-3e98451dfac3
kernel        /boot/vmlinuz-2.6.38-10-generic root=UUID=bfc79931-2ce4-449d-8a70-3e98451dfac3 ro quiet splash 
initrd        /boot/initrd.img-2.6.38-10-generic
quiet

title        Ubuntu 11.04, kernel 2.6.38-10-generic (recovery mode)
uuid        bfc79931-2ce4-449d-8a70-3e98451dfac3
kernel        /boot/vmlinuz-2.6.38-10-generic root=UUID=bfc79931-2ce4-449d-8a70-3e98451dfac3 ro  single
initrd        /boot/initrd.img-2.6.38-10-generic

title        Chainload into GRUB 2
root        bfc79931-2ce4-449d-8a70-3e98451dfac3
kernel        /boot/grub/core.img

title        Ubuntu 11.04, memtest86+
uuid        bfc79931-2ce4-449d-8a70-3e98451dfac3
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
--------------------------------------------------------------------------------

=========================== sda6/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root bfc79931-2ce4-449d-8a70-3e98451dfac3
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root bfc79931-2ce4-449d-8a70-3e98451dfac3
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 0,71,115; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root bfc79931-2ce4-449d-8a70-3e98451dfac3
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=bfc79931-2ce4-449d-8a70-3e98451dfac3 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root bfc79931-2ce4-449d-8a70-3e98451dfac3
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=bfc79931-2ce4-449d-8a70-3e98451dfac3 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root bfc79931-2ce4-449d-8a70-3e98451dfac3
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root bfc79931-2ce4-449d-8a70-3e98451dfac3
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root CE72CBC572CBB10F
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda4)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos4)'
    search --no-floppy --fs-uuid --set=root A2D0FC85D0FC60C9
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=========================== sda6/boot/burg/burg.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/burg-mkconfig using templates
# from /etc/burg.d and settings from /etc/default/burg
#

### BEGIN /etc/burg.d/00_header ###
set theme_name=burg
if [ -s $prefix/burgenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}
set gfxmode=1366x768
function select_menu {
  if menu_popup -t template_popup theme_menu ; then
    free_config template_popup template_subitem menu class screen
    load_config ${prefix}/themes/${theme_name}/theme ${prefix}/themes/custom/theme_${theme_name}
    save_env theme_name
    menu_refresh
  fi
}
function toggle_fold {
  if test -z $theme_fold ; then
    set theme_fold=1
  else
    set theme_fold=
  fi
  save_env theme_fold
  menu_refresh
}
function select_resolution {
  if menu_popup -t template_popup resolution_menu ; then
    menu_reload_mode
  fi
}
if test -f ${prefix}/themes/${theme_name}/theme ; then
  insmod coreui
  menu_region.text
  load_string '+theme_menu { -dark_shine { command="set theme_name=dark_shine" }}'
  load_string '+theme_menu { -minimal { command="set theme_name=minimal" }}'
  load_string '+theme_menu { -minimaltext { command="set theme_name=minimaltext" }}'
  load_string '+theme_menu { -vitruvio { command="set theme_name=vitruvio" }}'
  load_config ${prefix}/themes/conf.d/10_hotkey
  load_config ${prefix}/themes/${theme_name}/theme ${prefix}/themes/custom/theme_${theme_name}
  insmod vbe
  insmod png
  insmod jpeg
  set gfxfont="Unifont Regular 16"
  menu_region.gfx
  vmenu resolution_menu
  controller.ext
fi
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set bfc79931-2ce4-449d-8a70-3e98451dfac3
set locale_dir=($root)/boot/burg/locale
set lang=en
insmod gettext
set timeout=15
### END /etc/burg.d/00_header ###

### BEGIN /etc/burg.d/10_linux ###
menuentry 'Ubuntu GNU/Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os --group group_main {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set bfc79931-2ce4-449d-8a70-3e98451dfac3
    echo    'Loading Linux 2.6.38-10-generic ...'
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=bfc79931-2ce4-449d-8a70-3e98451dfac3 ro  quiet splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu GNU/Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os --group group_main {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set bfc79931-2ce4-449d-8a70-3e98451dfac3
    echo    'Loading Linux 2.6.38-10-generic ...'
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=bfc79931-2ce4-449d-8a70-3e98451dfac3 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-10-generic
}
### END /etc/burg.d/10_linux ###

### BEGIN /etc/burg.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/burg.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=bfc79931-2ce4-449d-8a70-3e98451dfac3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=743aed1b-6694-4e50-a185-4947370a1447 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 219.984889984 = 236.206977024  boot/burg/burg.cfg                             1
 211.779014587 = 227.395985408  boot/burg/core.img                             1
 207.696395874 = 223.012306944  boot/grub/core.img                             1
 211.851543427 = 227.473862656  boot/grub/grub.cfg                             1
 228.307144165 = 245.142929408  boot/grub/menu.lst                             1
 207.895496368 = 223.226089472  boot/grub/stage2                               1
 228.662109375 = 245.524070400  boot/initrd.img-2.6.38-10-generic              2
 228.377265930 = 245.218222080  boot/vmlinuz-2.6.38-10-generic                 2
 228.662109375 = 245.524070400  initrd.img                                     2
 228.662109375 = 245.524070400  initrd.img.old                                 2
 228.377265930 = 245.218222080  vmlinuz                                        2
 228.377265930 = 245.218222080  vmlinuz.old                                    2

=========================== sda8/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0, 8 )'
search --no-floppy --fs-uuid --set 27d965de-f62c-4689-a65b-7d8b3fb96f69
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1024x768
  set gfxpayload=keep
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0, 8 )'
search --no-floppy --fs-uuid --set 27d965de-f62c-4689-a65b-7d8b3fb96f69
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.38' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0, 8 )'
    search --no-floppy --fs-uuid --set 27d965de-f62c-4689-a65b-7d8b3fb96f69
    linux    /boot/vmlinuz-2.6.38 root=UUID=27d965de-f62c-4689-a65b-7d8b3fb96f69 ro   text splash nomodeset vga=791
    initrd    /boot/initrd.img-2.6.38
}
menuentry 'Ubuntu, with Linux 2.6.38 (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0, 8 )'
    search --no-floppy --fs-uuid --set 27d965de-f62c-4689-a65b-7d8b3fb96f69
    echo    'Loading Linux 2.6.38 ...'
    linux    /boot/vmlinuz-2.6.38 root=UUID=27d965de-f62c-4689-a65b-7d8b3fb96f69 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0, 8 )'
    search --no-floppy --fs-uuid --set 27d965de-f62c-4689-a65b-7d8b3fb96f69
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0, 8 )'
    search --no-floppy --fs-uuid --set 27d965de-f62c-4689-a65b-7d8b3fb96f69
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set CE72CBC572CBB10F
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda4)" {
    insmod ntfs
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set A2D0FC85D0FC60C9
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set bfc79931-2ce4-449d-8a70-3e98451dfac3
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=bfc79931-2ce4-449d-8a70-3e98451dfac3 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set bfc79931-2ce4-449d-8a70-3e98451dfac3
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=bfc79931-2ce4-449d-8a70-3e98451dfac3 ro single
    initrd /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda8/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=27d965de-f62c-4689-a65b-7d8b3fb96f69 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=557fe2bc-bc85-4dd8-b7c6-63bad8e4bbd8 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda8: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 241.414634705 = 259.216990208  boot/grub/core.img                             1
 241.930671692 = 259.771080704  boot/grub/grub.cfg                             1
 231.317634583 = 248.375418880  boot/initrdf.img-2.6.38                        1
 233.213188171 = 250.410754048  boot/initrd.img-2.6.38                         2
 231.347160339 = 248.407121920  boot/initrds.img-2.6.38                        1
 241.914287567 = 259.753488384  boot/vmlinuz-2.6.38                            1
 233.213188171 = 250.410754048  initrd.img                                     2
 241.914287567 = 259.753488384  vmlinuz                                        1

========= Devices which don't seem to have a corresponding hard drive: =========

sdb

```

Thanks again for your help.  Hope to hear back if you can possibly make anything of all this!

Ryan

---

### Post by drs305 on 2011-08-15
> **Ubunfoo said:**
> 
Thanks again for your help.  Hope to hear back if you can possibly make anything of all this!

Ryan,

1. Documenting things should make it a bit easier. Thanks for doing that.

2. Just a general observation: The conditional statement you tried to insert into 30_os-prober should be entered as in the example - the spaces are important and they must be included for the command to work properly (at least on my machines). In the script you may have done this, but in your last post all the spaces were stripped.
> if [ "$LONGNAME" = "Windows 7 (loader)" ] && [ "${DEVICE}" = "/dev/sda1" ]; then

It's possible the script is getting to this point of 30_os-prober and stopping because it can't run the line as entered, thus failing to enter the additional entries.

3. Also BURG uses several variables not in GRUB 2. I don't know if that is impacting the problem or not, but it might.

4. The main observation is that the boot info script reports that you are using Grub legacy. You will have to confirm or refute this. Or are you getting the Grub legacy menu and then chainloading into Grub 2 via the main menu. 

You can check this by running "grub-install -v". Grub legacy is 0.97 and Grub 2 is 1.98 or 1.99.

You can also check during boot by looking at the top of the Grub menu. The version should be displayed.

5. I have seen on the forums lately that the BURG creator is no longer maintaining BURG. Do you have a specific need for BURG? In it's day, it was a great leap forward for those wanting to use bootloader themes. GRUB has caught up a bit. If you don't have a specific need for BURG, you might consider reverting to Grub 2. 

I have the same general comment about using Grub legacy. Do you need Grub legacy to be able to recognize Backtract or have a special reason to use it? Chainloading to Grub 2 merely adds an extra level of complexity.

6. Let me know if adding the entries to 40_custom adds the items to your menu.

7. I can help you purge Grub legacy & BURG and add Grub 2 as the default, if that is what you want. You can also see if the conditionals *with the spaces* works any better.  I'm not a good script writer so rather than trying to figure out if BURG's differences are causing problems I'd first like to know what direction you want to take.

---

### Post by Ubunfoo on 2011-08-15
drs305, 

Great catch, haha.  I definitely didn't add the spaces correctly, and I'm sure you are right about the problems that was causing.  I'm still unsure why the problems would persist after the changes were reverted, but before trying that, I'll wait to hear back.

I am in fact using GRUB legacy at the moment.  I don't think I have always been using it, as GRUB looked a little different before I started using BURG and promptly messed it up, haha. I can't remember when exactly, but there was a period of time last night when every time I booted, I would have to press ESC within like 2 seconds or it would boot to kubuntu automatically.  If I managed to do it in time, I would get a really old looking version of GRUB I had never seen before.  It looked like it was 800x600 stretched out to my screen.  And yes, I do remember it giving me the option to chainload into another GRUB, but it would not actually complete the process.  It was missing a file, or couldn't read it, or something along those lines.  Sorry I can't be more specific, but it doesn't happen anymore. :D

Last night I found the Windows 7  menu entry in the grub.cfg file and added it to 40_custom and it booted! After fooling about for hours and finding it I yelled a victory cry - forgetting about my sleeping family members - and accidentally woke everyone up haha!  It's also worth mentioning that I looked everywhere I could think of, and can not find a similar menu entry for BackTrack 5, so it is still not on the menu.  Strange, I think.

As for ditching BURG and legacy, I would be perfectly fine with that to be honest.  I think I can manage getting rid of BURG, but I'm not sure how different purging grub is and installing grub 2 is, so I'll be looking into that until I hear back.

Thanks again, 

Ryan

---

### Post by drs305 on 2011-08-15
Ryan,

Let's go ahead then and purge Grub and BURG and change everything over to Grub 2. You might want to copy the /etc/grub.d folder and the /boot/grub folders and place them somewhere as a backup. That will at the very least preserve your current menuentries in case we have to retrieve them.

You should also copy the /etc/grub.d/40_custom file and put the copy somewhere else, such as on your Desktop or root's Desktop.

Purging and reinstalling Grub 2 from a working Ubuntu family OS is very easy to do. The only caveat is you want to make sure your Internet connection is working before you purge things - you will have to download Grub 2 and install in.

Boot to your working Ubuntu OS. Check your Internet connection, purge Grub legacy and Grub 2. I'm guessing on the BURG purge command, but assume it's correct. If it isn't, you can still run the others and I think G2 will override anything BURG has done:
```
sudo apt-get update  # Make sure Internet connection works
sudo apt-get purge burg
sudo apt-get purge grub-common # This should remove grub-common, grub, & grub-pc (GRUB 2)
sudo apt-get install grub-pc # This should install Grub 2 (grub-common & grub-pc)

```
As they install, it will first ask if you want to include any kernel options. Normally if you are using them, you would already know what they are. If you don't want to add any, TAB to OK and ENTER.

Next you will be asked for the boot drive. Use the SPACEBAR to select  B]sda[/B] and TAB to OK and ENTER. Do NOT select any partition if one is presented.

Grub 2 should install and run "update-grub". It should find Windows. Watch the terminal to see if it runs update-grub and also locates Windows. I don't know what it will do with Backtrack, but we'll see.

When finished it should have the OS you are currently running as the default OS, with recovery, memtest and hopefully Windows boot options. Reboot and make sure Ubuntu boots (and Windows if found). If Windows isn't found, run "sudo update-grub" again.

You can try to make your tweaks/edits again. If you run into problems run the boot info script again and post the new results.

If you have questions go ahead an ask.

---

### Post by Ubunfoo on 2011-08-16
drs305, 

Awesome, that worked like a dream.  Thanks!  I should be able to follow your guide through renaming the grub2 menu items now, right?  Remembering to add spaces in that line of script of course.  

Ryan

---

### Post by drs305 on 2011-08-16
> **Ubunfoo said:**
> drs305, 

Awesome, that worked like a dream.  Thanks!  I should be able to follow your guide through renaming the grub2 menu items now, right?  Remembering to add spaces in that line of script of course.  

Ryan

Glad it worked. :-)

Yes, the tweaks should now work. The disclaimer is that the devs continue to improve the Grub scripts. I've tried to keep the tweaks up to date with the changes I'm aware of ...

---

### Post by candtalan on 2011-09-16
> **Darktrax said:**
>  Don't get me wrong folks - I am all agreed that the experts have done great work to make a new system with all kinds of benefits, even if mostly useful to other experts. I just think they lost sight of the needs of the ultimate user. I need a ***low risk*** tool to make an initial menu I want, maybe with ways to make it open further to display memory testing and recover options. For now, I have to settle for a little *Post-It* note that decodes which option is actually Ubuntu-Studio, PureDyne, etc.  among other OS kernels.

I very much have the same view. I have just installed a second vista machine for  friend/s with Ubuntu 10.x and although on the first one I did manage to create a custom menu which did the trick to reverse the Vista recovery vista loader titles appropriately, that was a few months ago. With the second different install, I get the same problem, and while I now know what the problem is, I have forgotten the exact solution (!) OK, I can follow links and again temporarily become familiar with Grub2, but I simply have run out of time. The laptop owner has now collected it, knowing the titles for vista are wrong. He accepts this. However I know that his son is pressuring him to get a Mac and not bother to mess with (difficult) Linux.....
I think he will persist but I yearn for practical and user friendly solutions to problems like this.

---

### Post by drs305 on 2011-09-16
*candtalan* and others,

Don't forget there are two great GUI tools available now that weren't when all these guides were originally written:

[_*Grub Customizer*_]("http://ubuntuforums.org/showthread.php?t=1664134"): It can change the menu order, titles, hide entries, and a lot more. It can accomplish almost all the tweaks I've ever covered.

[_*Boot Repair*_]("http://ubuntuforums.org/showthread.php?t=1831869"): If Grub 2 is broken, this app has a good chance of being able to fix it. It also provides an option to retrieve and run the boot info script for you, which is a script we often ask users to run when we are troubleshooting Grub 2 problems.

---

### Post by candtalan on 2011-09-16
> **drs305 said:**
> *candtalan* and others,

Don't forget there are two great GUI tools available now that weren't when all these guides were originally written:

[_*Grub Customizer*_]("http://ubuntuforums.org/showthread.php?t=1664134"): It can change the menu order, titles, hide entries, and a lot more. It can accomplish almost all the tweaks I've ever covered.

[_*Boot Repair*_]("http://ubuntuforums.org/showthread.php?t=1831869"): If Grub 2 is broken, this app has a good chance of being able to fix it. It also provides an option to retrieve and run the boot info script for you, which is a script we often ask users to run when we are troubleshooting Grub 2 problems.

Thanks! Will give them a good try.

---

### Post by bachor on 2011-10-14
Thank You drs305 :P

Thanks to your help I was able to easy remove "MEMTEST86+", hide Windows 7 recovery entry, change Windows 7 name and eliminate "(sda)" in my dualboot Win 7 with Xubuntu 11.04 [Grub2]

):P

---

### Post by linuxaddix on 2011-10-17
thats a lot of work if you ask me the simplest way i did mine is right here:

nstall Instructions:
Open Synaptic Package Manager and Add repository:
ppa:ingalex/super-boot-manager
sudo apt-get install "super-boot-manager"

after thats done go into accessories and it'll be there ...superboot manager
be careful when using this you need to do it with the one that has /dev after the headers if you're dual-booted
single boot not to worry.and its simple.
as far as hiding memtest just go to synaptics and remove it
enjoy

---

### Post by c.cobb on 2011-12-21
> **drs305 said:**
> 
[QUOTE=moonlight_sonata;10478359]
how to change GRUB Title (GNU GRUB Version 1.97, Ubuntu) become my Distro name?

I have found several files in the Grub2 libraries that define the title during the running of scripts, but I haven't been able to find the one that actually changes the title. It's possible that the main title is not editable via any normal means by the user. 

If you find an answer please let us know.[/QUOTE]

What's your definition of normal? ;-) And are you still interested in a solution?

I suppose that recompiling Grub2 would be one possibility, but that's kinda boring! Another way is to patch the binary file that has the menu title string. If you do this with Grub 1.99, you will have 32 characters to work with. See attached screen shot.

Here's a quick how to, and some fun for a rainy afternoon.
```

> sudo apt-get install ncurses-hexedit

> cp /boot/grub/normal.mod /tmp

> hexeditor /tmp/normal.mod  
                             /-------------------------------
0000D740  6E 6D 65 6E  74 00 47 4E   55 20 47 52  55 42 20 20   nment.GNU GRUB
0000D750  76 65 72 73  69 6F 6E 20   **25 73 00** 31  2E 39 39 2D   version %s.1.99-
0000D760  31 32 75 62  75 6E 74 75   35 00 00 3E  00 67 72 75   12ubuntu5..>.gru
          ---------------------------/

```Note the characters "**25 73 00**" the middle of the string. It would be best to leave these unchanged and wrap your new title around this part. 

If you run the ncurses hexeditor, use Ctrl+W to search for the title string. Use Ctrl+C to bail out without saving, and Ctrl+X to save the changes. (You did make a backup copy, right?) Also handy to have is a page of [Ascii character codes]("http://www.ascii.cl/htmlcodes.htm") open while you're editing.
Enjoy,

p.d. I thought about including the patched normal.mod file here, but would rather not be the source of unsupported junk in this forum. Besides, what else were you going to do today?

---

### Post by jwestbury on 2011-12-28
After much hair-pulling, I found this thread, which seems to have fixed my issue with being unable to get a hidden Grub menu when using multiple operating systems.

Unfortunately, this seems to have had a strange side effect, or else I made some other mistake in my Grub configuration: Now, my splash screen will not display until I press a key -- before that, it will just display a blank screen, and eventually boot into the default menu option.

I'm trying to display a splash screen, providing the user a prompt to hold Shift in order to display the Grub menu -- Ubuntu (Lucid) will boot, launch a script, and perform and automated restore of a Windows partition image, if the user selects this option, otherwise it will boot into Windows.

Is there any way to have the splash screen display properly (that is, without pressing a key) while doing the multi-OS hidden thing? (I believe "thing" is the technical term here, yes?)

---

### Post by drs305 on 2011-12-29
> **jwestbury said:**
> After much hair-pulling, I found this thread, which seems to have fixed my issue with being unable to get a hidden Grub menu when using multiple operating systems.

Unfortunately, this seems to have had a strange side effect, or else I made some other mistake in my Grub configuration: Now, my splash screen will not display until I press a key -- before that, it will just display a blank screen, and eventually boot into the default menu option.

I'm trying to display a splash screen, providing the user a prompt to hold Shift in order to display the Grub menu -- Ubuntu (Lucid) will boot, launch a script, and perform and automated restore of a Windows partition image, if the user selects this option, otherwise it will boot into Windows.

Is there any way to have the splash screen display properly (that is, without pressing a key) while doing the multi-OS hidden thing? (I believe "thing" is the technical term here, yes?)

jwestbury

Welcome to the Ubuntu Forums.  :-)

I'm not sure I understand your request completely, but I think you want a first screen with only an instruction and then would boot to a selection if nothing is done?

One way to set it up is to have the first menu contain just two entries. The first would be a menuentry which takes you to another Grub 2 menu. You could make the menuentry title "Select this line and press any key to view the Grub 2 menu" or whatever, and then construct the menuentry to open another menu (configfile mygrub.cfg). 

The second menu entry could have a blank title so it couldn't be seen (but could be selected if the user cursored down and pressed ENTER). You would set this entry as the default one to boot after the desired timeout.

This first menu would have to be a custom entry, although the second could be the standard menu generated by Grub. You could update the real Grub 2 menu, if it was called mygrub.cfg, by running "sudo grub-mkconfig -o mygrub.cfg"

You would have a few problems with grub/kernel updates that would overwrite your custom 'grub.cfg' unless you disable the update-grub command entirely or redirect it to act on 'mygrub.cfg'. 

I won't research the specifics since I'm not even sure this is what you are envisioning.

---

### Post by jwestbury on 2011-12-29
That's an interesting approach. Thanks for the idea -- I'll give it a shot.

Updates won't really be an issue -- the primary boot option is going to be Windows, and the second boot option is going to be Ubuntu, in the form of Turnkey Core (so, console only), which is going to exist solely to restore an image of the original Windows configuration. So, it won't be running, and when it does, it will immediately run a script to restore an image, then prompt the user to reboot. Unless they send a sigint, they'll never even see that Ubuntu exists.

So, my menu entry would look something like this?

```
menuentry "Title goes here" {
    configfile (hdx,y)/boot/grub/othergrub.cfg
}
```

---

### Post by drs305 on 2011-12-30
> **jwestbury said:**
> That's an interesting approach. Thanks for the idea -- I'll give it a shot.
...
So, my menu entry would look something like this?

```
menuentry "Title goes here" {
    configfile (hdx,y)/boot/grub/othergrub.cfg
}
```

Yes, but add a second entry for the one you want as the default to boot after a time period if no action is taken. You can leave the title blank ( "" ) so the user won't see it, although it *would* be available if the user moved the cursor to the blank line. 

If that concerns you, you could take it a step further and add password protection. Here is a link to a thread I wrote about passwords:
[http://ubuntuforums.org/showthread.php?t=1369019]("http://ubuntuforums.org/showthread.php?t=1369019")

---

### Post by jwestbury on 2011-12-30
Okay, so, there's actually another method which your response put me on to. The original issue is that the splash screen wouldn't show until I pressed a key, which kind of defeated my purpose for it.

However, there's an easy solution for that, as it turns out.

I now have the following menuentries:

**in /boot/grub/grub.cfg:**

```
menuentry "Other menu" {
    configfile (hd0,1)/boot/grub/othergrub.cfg
}
```

**in /boot/grub/othergrub.cfg:**

```
menuentry "Microsoft Windows XP Professional" {
    *Windows stuff here*
}

menuentry "Recovery mode" {
    *Linux stuff here*
}
```

For the grub.cfg, both timeouts are set to 0, and it defaults to, obviously, menu selection 1.

For othergrub.cfg, there is a hidden timeout of 6, defaulting to Windows XP.

I'm not sure exactly why, but when othergrub.cfg is loaded by grub.cfg, the splash screen -- which tells the user to hold shift -- comes up fine. It's kind of a funky workaround, but it works.

So, if anyone else ever runs into the same problem, there you go!

[Edit: Thanks, drs305!]

---

### Post by dc_wmj2 on 2012-01-28
> > sudo apt-get install ncurses-hexedit

> cp /boot/grub/normal.mod /tmp

> hexeditor /tmp/normal.mod  
                             /-------------------------------
0000D740  6E 6D 65 6E  74 00 47 4E   55 20 47 52  55 42 20 20   nment.GNU GRUB
0000D750  76 65 72 73  69 6F 6E 20   **25 73 00** 31  2E 39 39 2D   version %s.1.99-
0000D760  31 32 75 62  75 6E 74 75   35 00 00 3E  00 67 72 75   12ubuntu5..>.gru
          ---------------------------/I tried editing the normal.mod-file like this - and changing the title works perfectly for me.
But how do I insert some new-lines into grub, so that the whole box will move down? My background-image has a title and the grub-box is covering it.
I tried inserting the Hex-Codes 0A (for \n) and 0D (for Enter) but no success. The title  just got left-aligned afterwards.

Also searching for the Hex-Combination DAC4 (to get the upper-left-corner of the box) did return a result. However, new-lines didn't cause an effect at all.
How can I move the whole menu down a few lines? In a 2nd attempt DAC4 was not in the file - maybe it wasn't the addres of the box.

---

### Post by drs305 on 2012-01-28
> **dc_wmj2 said:**
> 
How can I move the whole menu down a few lines? In a 2nd attempt DAC4 was not in the file - maybe it wasn't the addres of the box.

I know the Grub 2 menu location was originally hard coded and don't know if it's changed. You appear to know a lot more about editing the code than I do. :-)  All I know how to do is modify the background image to accommodate the menu structure. :-(

Good luck with your endeavor. If you find an answer please share it with us.

---

### Post by dc_wmj2 on 2012-01-28
Ladies and gentleman... I proudly present: My selfmade Grub1.98-bootloader - including title-hack:

[[IMG]http://s15.postimage.org/6iy18v9w7/qemusnapshot2.jpg[/IMG]]("http://postimage.org/image/6iy18v9w7/")

Since my programming knowledge is extremely low, I just designed a proper background-image fitting into the ugly menu. Now the title is a bit small and the menu-entries are still too high - but I think the rest is okay. Is there at least a way to include empty menu-entries at the top? In grub1 this was no problem.

---

### Post by drs305 on 2012-01-28
Nice looking screen.

You can move the visible entries down a bit by adding blank menuentries. I've added 2 in the example.

> menuentry ' '  --class ubuntu --class gnu-linux --class gnu --class os {
	insmod ext2
}

menuentry ' '  --class ubuntuX --class gnu-linux --class gnu --class os {
	insmod ext2
}


Explanation:
The menuentries appear to need at least one command line or an error message will be generated and grub.cfg won't be updated. I've added 'insmod ext2' but others can be used as well. 

These menuentries should be added to /etc/grub.d/09_custom so they appear before any other sections in the grub.cfg file. This will cause the blanks to be added at the top of the menu. You can create other gaps between menus (10, 30 for instance) by creating additiona X9_custsom files. 

You can make the custom file by copying the /etc/grub.d/40_custom file, renaming it to 09_custom. Make it executable so it will be included when "update-grub" is run.

Don't forget to update the default # or title in /etc/default/grub so the proper menuentry is designated the default.

---

### Post by dc_wmj on 2012-01-28
That's what I was looking for. Cool you answered so fast. Is there also a way to automatically indent entrys by some number of spaces? E.g. every line beginning with 10 spaces? In grub1 "sub-menus" became common this way. They indented all lines and drew an ascii-rectangle around -> submenu in the bootloader. 

I'm still tweaking around at my background-picture and have trouble getting proper png's. Sometimes they work - sometimes they don't. I actually never change the settings when exporting them. Somebody knows grubs png-limitation?

---

### Post by drs305 on 2012-01-28
> **dc_wmj said:**
> That's what I was looking for. Cool you answered so fast. Is there also a way to automatically indent entrys by some number of spaces? E.g. every line beginning with 10 spaces? In grub1 "sub-menus" became common this way. They indented all lines and drew an ascii-rectangle around -> submenu in the bootloader. 

I'm still tweaking around at my background-picture and have trouble getting proper png's. Sometimes they work - sometimes they don't. I actually never change the settings when exporting them. Somebody knows grubs png-limitation?

You can hack the indentation by adding spaces in the title - it's crude but it works if you are using a custom menu.

If you want to incorporate it into the automatic menu generation it would be possible to hack the scripts to add before the title. I'd have to poke around a bit but am sure I could figure it out. Just let me know.

For now, on a custom menu (or in grub.cfg until overwritten) you would just make the menuentry title:
```
"    Ubuntu....."
*rather than*
"Ubuntu"


```
**Added: I always forget we now have Grub Customizer, which easily allows manual title changes. See the link in my signature line. You could manually add the spaces there.**

I wrote a guide about Grub 1.99 backgrounds that might help you a bit in your tweaking.
[Grub 2 Drop-In Backgrounds & Font Selection]("http://ubuntuforums.org/showthread.php?t=1739412")

As far as the PNG images, make sure they are RGB, non-indexed. If you use GIMP, you can check/change via Image > Mode menu selection.

---

### Post by drs305 on 2012-01-28
I checked the Grub 2 scripts. To alter the Grub 2 menuentries for your main Ubuntu OS, you would edit the /etc/grub.d/10_linux script:

```
sudo cp /etc/grub/10_linux /etc/grub.d/10_linux.bak
sudo cp /etc/grub/30_os-prober /etc/grub.d/30_os-prober.bak
gksu gedit +85 /etc/grub.d/10_linux & gksu gedit +184 /etc/grub.d/30_os-prober &

```
The first command makes a backup.
The second commands opens 10_linux near the line you need to edit. I may have modified the scripts so your line numbers may be lower. I'm using Grub 1.99.

In the example below, I've changed the main entry but left the Recovery option unchanged so you can see the difference. You would most likely want to change both.

```
  if ${recovery} ; then
    title=[COLOR="DarkRed"]"$(gettext_quoted[/COLOR] "%s, with Linux %s (recovery mode)")"
  else
    title=[COLOR="DarkRed"]"     $(gettext_quoted [/COLOR]"%s, with Linux %s")"
  fi

```
Save the file and update-grub.

I don't have Windows loaded on my current machine, but I think these are the lines you would alter in 30_os-prober and add spaces immediately before $LONGNAME:
```

      found_other_os=1
      cat << EOF
menuentry [COLOR="DarkRed"]"${LONGNAME} [/COLOR](on ${DEVICE})" --class windows --class os {
EOF

```
Several 'agains': 
Save and update-grub. 
I can't verify it since I have no Windows entries, so if it doesn't work, let me know.
Grub Customizer can manually edit the title if this doesn't work.

If the scripts are updated you will need to make the changes to the scripts again, but they shouldn't change too often.

---

### Post by hal8000 on 2012-04-06
Thank you drs305 for all your hard work on this thread and Grub2.

There is an error in the os-prober scripts that fails to proberly detect other linux systems that use grub legacy.

This detection error has also been migrated into the burg bootloader.
Here is an extract from my /boot/grub/grub.cfg to show the problem:


cat /boot/grub/brub.cfg
--snip--

menuentry "PCLinuxOS 2011 (on /dev/sdb9)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos9)'
	search --no-floppy --fs-uuid --set=root 8dc93899-0533-4c01-a990-7105cf6052c2
	linux /boot/vmlinuz BOOT_IMAGE=PCLinuxOS_2011 root=/dev/sdb1 splash vga=794
	initrd /boot/initrd.img
}

menuentry "PCLinuxOS 2011 (on /dev/sda10)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root bda8695c-bbb7-4eec-89c7-0e2f7ca94cd0
	linux /boot/vmlinuz BOOT_IMAGE=PCLinuxOS_2011 root=/dev/sdb1 splash vga=794
	initrd (hd1,[COLOR="Red"]0[/COLOR])/boot/initrd.img
}
menuentry "Ubuntu Oneric (on /dev/sda10)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root bda8695c-bbb7-4eec-89c7-0e2f7ca94cd0
	linux /boot/vmlinuz root=/dev/sda8 ro splash vga=0x0324
	initrd (hd0,7)/boot/initrd.img
}
menuentry "Suse 11.4 (on /dev/sda10)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root bda8695c-bbb7-4eec-89c7-0e2f7ca94cd0
	linux /boot/vmlinuz-2.6.37.6-0.7-desktop root=/dev/disk/by-id/ata-WDC_WD5001AALS-00J7B0_WD-WMATV7661868-part10 splash=silent quiet showopts vga=0x31a
	initrd /boot/initrd-2.6.37.6-0.7-desktop
}
--snip--

In short I have 8 distributions installed across 2 hard drives including
FreeBSD.
Grub2 os-prober never picks up FreeBSD but worst still, see the highlighted
entry in red, for PCLinux.

Partition (hd1,0) cannot exist in Grub2, as partition counting starts at 1.

The result, 2 bootable operating systems, the rest failed to properly detect. 

My solution is to disable os-prober and manually create custom scripts.

In actual fact, I choose to use grub-legacy as its much easier and a single configuration file and its easier to theme and change fonts, etc as well.

However if work continues on grub2 and burg then I will be forced into using grub2.

I decided to try burg, but again Ubuntu,linux 3.0.0 on /dev/sdx
as a name drives me crazy, I prefer shorter names.

Your guides are compatible with burg, /etc/defaults/grub being equivalent to /etc/defaults/burg and scripts in burg are at /etc/burg.d/

There are slight differences in burg for the Icon that preceds the title:
example /etc/burg/40_script below:

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "PCLinuxOS 2011" --class pclinuxos --class os {
	insmod ext2
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root 09513d2f-941d-49eb-bc32-0dfe134bedb9
	linux /boot/vmlinuz BOOT_IMAGE=PCLinuxOS_2011 root=/dev/sdb1 splash vga=794
	initrd (hd1,1)/boot/initrd.img
}


The --class pclinuxos  creates an icon for the menu entry in Burg.
Hope this helps someone, or please move the thread if you dont think it is appropriate here.
Regards h8k

---

### Post by drs305 on 2012-04-07
> **hal8000 said:**
> 
There is an error in the os-prober scripts that fails to proberly detect other linux systems that use grub legacy.
...

This detection error has also been migrated into the burg bootloader.
The --class pclinuxos  creates an icon for the menu entry in Burg.
Hope this helps someone, or please move the thread if you dont think it is appropriate here.
Regards h8k

Thanks for sharing that information. I don't think BURG is being actively developed any longer but I know a lot of users still take advantage of it's theming capabilities.

I'd suggest you file a bug report but the Grub2 devs don't seem to spend much time trying to rectify Grub legacy issues any longer. Your approach of making custom menus is at least a good workaround.

---

### Post by hal8000 on 2012-04-11
Thank you DRS, will post a bug report.

I have also found that by disabling os-prober in Grub2 or Burg and manually creating custom scripts in /etc/grub.d/ or /etc/burg.d/ the bootloader appears almost instantly.

When os-prober has been used, /bott/grub/grub.cfg is much larger and think the delay (of about 1/2 second) is due to grub.cfg being parsed.

---

### Post by Redsandro on 2012-04-20
I cannot seem to hide my bootmenu in Ubuntu 12.04.

This method used to work in Ubuntu 10.04, and it seems to be still valid when you look at the code, but I can't get it (not) to work anymore.

I want to see only my other OSses only when I hold 'shift'.

> **drs305 said:**
> 
[SIZE=3]**11. [COLOR=DarkRed]HIDING THE MENU ON MULTI-OS SYSTEMS[/COLOR]**[/SIZE]
By design, Grub 2 allows hiding the menu only on single-OS systems. This is established in the */etc/grub.d/30_os-prober* file. For users with multiple OS's on their machines, hiding the menu can be accomplished by altering the scripts. There are two ways to accomplish the task. The first edits only one file and eliminates a conditional; the second edits two files and adds a conditional, but is a bit more 'elegant'.

Shown are the applicable sections. Changes are highlighted in [COLOR="Red"]**bold red**[/COLOR]. The lines between the altered lines have been omitted.
[LIST]
[*]**Method 1.** Remove a conditional from */etc/grub.d/30_os-prober*.
For both Grub 1.97~beta (Karmic) and 1.98 (Lucid & later), the first line to edit is the same. It appears at approximately line 25-30 of */etc/grub.d/30_os-prober* in both versions.

The second change is to place a **[COLOR="DarkRed"]#[/COLOR]** symbol at the end of the conditional. There are many *if* statements, and it's important to find the correct nested *fi*. 

In Karmic, the nested *fi* comes just before the "GRUB_DISABLE_PROBER" section. If Lucid and later, it preceeds the "() adjust timeout" section.
Karmic (Grub 1.97~beta):

Lucid & later (Grub 1.98+):


[*]**Method 2.** Add a conditional.
This procedure modifies both */etc/grub.d/30_os-prober* and */etc/default/grub*. Open both with:
```
gksu gedit /etc/default/grub /etc/grub.d/30_os-prober
```
Add this line to */etc/default/grub*:

Change this line in */etc/grub.d/30_os-prober*, approximately line 25-30, 
From this:

To this:

[/LIST]

Tiny rewrite, someone? :p

---

### Post by Dareus on 2012-07-09
> I cannot seem to hide my bootmenu in Ubuntu 12.04.

This method used to work in Ubuntu 10.04, and it seems to be still valid when you look at the code, but I can't get it (not) to work anymore.

I want to see only my other OSses only when I hold 'shift'.

Just BUMPING Redsandro's request ;P

---

### Post by drs305 on 2012-07-09
> **Dareus said:**
> Just BUMPING Redsandro's request ;P

Which version of Ubuntu/Grub are you using:
```
sudo lsb_release -c && grub-install -v
```

---

### Post by Dareus on 2012-07-09
> **drs305 said:**
> Which version of Ubuntu/Grub are you using

Codename:	precise
grub-install (GRUB) 1.99-21ubuntu3.1

I tried the more elegant way: I found some problems identifying the correct conditional switch and what I had is that I wasn't able to get the menu even if I press every key on the keyboard (SHIFT, ESC, etc.)

My 30_os-prober looks like this
```

$ cat /etc/grub.d/30_os-prober
#! /bin/sh
set -e

# grub-mkconfig helper script.
# Copyright (C) 2006,2007,2008,2009  Free Software Foundation, Inc.
#
# GRUB is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# GRUB is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with GRUB.  If not, see <http://www.gnu.org/licenses/>.

prefix="/usr"
exec_prefix="${prefix}"
datarootdir="${prefix}/share"

. "${datarootdir}/grub/grub-mkconfig_lib"

found_other_os=

make_timeout () {
  if [ "x${found_other_os}" = "x" ] ; then
    if [ "x${1}" != "x" ] ; then
      if [ "x${GRUB_HIDDEN_TIMEOUT_QUIET}" = "xtrue" ] ; then
	verbose=
      else
	verbose=" --verbose"
      fi

      if [ "x${1}" = "x0" ] ; then
	cat <<EOF
if [ "x\${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep$verbose --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
EOF
      else
	cat << EOF
if [ "x\${timeout}" != "x-1" ]; then
  if sleep$verbose --interruptible ${GRUB_HIDDEN_TIMEOUT} ; then
    set timeout=0
  fi
fi
EOF
      fi
    fi
  fi
}

adjust_timeout () {
  if [ "x$GRUB_BUTTON_CMOS_ADDRESS" != "x" ]; then
    cat <<EOF
if cmostest $GRUB_BUTTON_CMOS_ADDRESS ; then
EOF
    make_timeout "${GRUB_HIDDEN_TIMEOUT_BUTTON}" "${GRUB_TIMEOUT_BUTTON}"
    echo else
    make_timeout "${GRUB_HIDDEN_TIMEOUT}" "${GRUB_TIMEOUT}"
    echo fi
  else
    make_timeout "${GRUB_HIDDEN_TIMEOUT}" "${GRUB_TIMEOUT}"
  fi
}

[B]#if [ "x${GRUB_DISABLE_OS_PROBER}" = "xtrue" ]; then EDIT to correct hidden menu from: http://ubuntuforums.org/showthread.php?t=1287602
if [ "x${found_other_os}" = "x" ] || [ "x${GRUB_FORCE_HIDDEN_MENU}" = "xtrue" ] ; then 
  adjust_timeout
  exit 0
fi[/B]

if [ -z "`which os-prober 2> /dev/null`" -o -z "`which linux-boot-prober 2> /dev/null`" ] ; then
  # missing os-prober and/or linux-boot-prober
  adjust_timeout
  exit 0
fi

OSPROBED="`os-prober | tr ' ' '^' | paste -s -d ' '`"
if [ -z "${OSPROBED}" ] ; then
  # empty os-prober output, nothing doing
  adjust_timeout
  exit 0
fi

osx_entry() {
	found_other_os=1
        cat << EOF
menuentry "${LONGNAME} (${2}-bit) (on ${DEVICE})" --class osx --class darwin --class os {
EOF
	save_default_entry | sed -e "s/^/\t/"
	prepare_grub_to_access_device ${DEVICE} | sed -e "s/^/\t/"
	cat << EOF
        load_video
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ \$do_resume = 0 ]; then
           xnu_uuid ${OSXUUID} uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           $1 /mach_kernel boot-uuid=\${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
EOF
}

wubi=

for OS in ${OSPROBED} ; do
  DEVICE="`echo ${OS} | cut -d ':' -f 1`"
  LONGNAME="`echo ${OS} | cut -d ':' -f 2 | tr '^' ' '`"
  LABEL="`echo ${OS} | cut -d ':' -f 3 | tr '^' ' '`"
  BOOT="`echo ${OS} | cut -d ':' -f 4`"

  if [ -z "${LONGNAME}" ] ; then
    LONGNAME="${LABEL}"
  fi

  echo "Found ${LONGNAME} on ${DEVICE}" >&2

  case ${BOOT} in
    chain)

      case ${LONGNAME} in
	Windows*)
	  if [ -z "$wubi" ]; then
	    if [ -x /usr/share/lupin-support/grub-mkimage ] && \
	       /usr/share/lupin-support/grub-mkimage --test; then
	      wubi=yes
	    else
	      wubi=no
	    fi
	  fi
	  if [ "$wubi" = yes ]; then
	    echo "Skipping ${LONGNAME} on Wubi system" >&2
	    continue
	  fi
	  ;;
      esac

      found_other_os=1
      cat << EOF
menuentry "${LONGNAME} (on ${DEVICE})" --class windows --class os {
EOF
      save_default_entry | sed -e "s/^/\t/"
      prepare_grub_to_access_device ${DEVICE} | sed -e "s/^/\t/"

      case ${LONGNAME} in
	Windows\ Vista*|Windows\ 7*|Windows\ Server\ 2008*)
	;;
	*)
	  cat << EOF
	drivemap -s (hd0) \${root}
EOF
	;;
      esac

      cat <<EOF
	chainloader +1
}
EOF
    ;;
    linux)
      LINUXPROBED="`linux-boot-prober ${DEVICE} 2> /dev/null | tr ' ' '^' | paste -s -d ' '`"
      prepare_boot_cache=

      for LINUX in ${LINUXPROBED} ; do
        LROOT="`echo ${LINUX} | cut -d ':' -f 1`"
        LBOOT="`echo ${LINUX} | cut -d ':' -f 2`"
        LLABEL="`echo ${LINUX} | cut -d ':' -f 3 | tr '^' ' '`"
        LKERNEL="`echo ${LINUX} | cut -d ':' -f 4`"
        LINITRD="`echo ${LINUX} | cut -d ':' -f 5`"
        LPARAMS="`echo ${LINUX} | cut -d ':' -f 6- | tr '^' ' '`"

        if [ -z "${LLABEL}" ] ; then
          LLABEL="${LONGNAME}"
        fi

	if [ "${LROOT}" != "${LBOOT}" ]; then
	  LKERNEL="${LKERNEL#/boot}"
	  LINITRD="${LINITRD#/boot}"
	fi

	if [ -z "${prepare_boot_cache}" ]; then
	  prepare_boot_cache="$(prepare_grub_to_access_device ${LBOOT} | sed -e "s/^/\t/")"
	  [ "${prepare_boot_cache}" ] || continue
	fi
	found_other_os=1
        cat << EOF
menuentry "${LLABEL} (on ${DEVICE})" --class gnu-linux --class gnu --class os {
EOF
	save_default_entry | sed -e "s/^/\t/"
	printf '%s\n' "${prepare_boot_cache}"
	cat <<  EOF
	linux ${LKERNEL} ${LPARAMS}
EOF
        if [ -n "${LINITRD}" ] ; then
          cat << EOF
	initrd ${LINITRD}
EOF
        fi
        cat << EOF
}
EOF
      done
    ;;
    macosx)
      OSXUUID="`grub-probe --target=fs_uuid --device ${DEVICE} 2> /dev/null`"
      osx_entry xnu_kernel 32
      osx_entry xnu_kernel64 64
    ;;
    hurd)
      found_other_os=1
      cat << EOF
menuentry "${LONGNAME} (on ${DEVICE})" --class hurd --class gnu --class os {
EOF
      save_default_entry | sed -e "s/^/\t/"
      prepare_grub_to_access_device ${DEVICE} | sed -e "s/^/\t/"
      grub_device="`${grub_probe} --device ${DEVICE} --target=drive`"
      mach_device="`echo "${grub_device}" | sed -e 's/(\(hd.*\),msdos\(.*\))/\1s\2/'`"
      grub_fs="`${grub_probe} --device ${DEVICE} --target=fs`"
      case "${grub_fs}" in
	*fs)	hurd_fs="${grub_fs}" ;;
	*)	hurd_fs="${grub_fs}fs" ;;
      esac
      cat << EOF
	multiboot /boot/gnumach.gz root=device:${mach_device}
	module /hurd/${hurd_fs}.static ${hurd_fs} --readonly \\
			--multiboot-command-line='\${kernel-command-line}' \\
			--host-priv-port='\${host-port}' \\
			--device-master-port='\${device-port}' \\
			--exec-server-task='\${exec-task}' -T typed '\${root}' \\
			'\$(task-create)' '\$(task-resume)'
	module /lib/ld.so.1 exec /hurd/exec '\$(exec-task=task-create)'
}
EOF
    ;;
    *)
      echo "  ${LONGNAME} is not yet supported by grub-mkconfig." >&2
    ;;
  esac
done

adjust_timeout

```

---

### Post by drs305 on 2012-07-09
Dareus,

For GRUB 1.99, I changed line 29 of /etc/grub.d/30_os-prober:
> make_timeout () {
  if [ "x${found_other_os}" = "x" ]**[COLOR="DarkRed"] || [ "x${GRUB_FORCE_HIDDEN_MENU}" = "xtrue" ][/COLOR]** ; then 

I added these lines to the bottom of /etc/default/grub:
> GRUB_FORCE_HIDDEN_MENU="true"
export GRUB_FORCE_HIDDEN_MENU
Save both files and update-grub.

On my machine the system no longer displays the menu.

---

### Post by Dareus on 2012-07-09
Ok, I had modified the wrong block :P

Anyway, my menu is not showing now on boot but I can't get it to appear using SHIFT or any other key!

---

### Post by drs305 on 2012-07-09
> **Dareus said:**
> Ok, I had modified the wrong block :P

Anyway, my menu is not showing now on boot but I can't get it to appear using SHIFT or any other key!

The format of the 30_os-prober script makes the 'timeout' section appear to be independent of whether another os is found, but it is.

To correct this, in the same section you just modified, place the following immediately after the timeout funtion:

> make_timeout () {
[COLOR="DarkRed"]if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep$verbose --interruptible 3 ; then
      set timeout=0
    fi
  fi[/COLOR]
if [ "x${found_other_os}" = "x" ] || [ "x${GRUB_FORCE_HIDDEN_MENU}" = "xtrue" ] ; then 

This should enable the SHIFT and ESC keys.

I've never understood why this feature was placed in the 30_... script and not the main script.

---

### Post by Dareus on 2012-07-09
are you sure this line is correct? 
```
if sleep$verbose --interruptible 3 ; then
```

I get an error when running update-grub

My 30_os-prober looks like this:
```

#! /bin/sh
set -e

# grub-mkconfig helper script.
# Copyright (C) 2006,2007,2008,2009  Free Software Foundation, Inc.
#
# GRUB is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# GRUB is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with GRUB.  If not, see <http://www.gnu.org/licenses/>.

prefix="/usr"
exec_prefix="${prefix}"
datarootdir="${prefix}/share"

. "${datarootdir}/grub/grub-mkconfig_lib"

found_other_os=

make_timeout () {
###EDIT following block put here to have the key to show the menu
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep$verbose --interruptible 3 ; then
      set timeout=0
    fi
  fi
###
#  if [ "x${found_other_os}" = "x" ] ; then EDIT to have the hidden menu working
  if [ "x${found_other_os}" = "x" ] || [ "x${GRUB_FORCE_HIDDEN_MENU}" = "xtrue" ] ; then 
    if [ "x${1}" != "x" ] ; then
      if [ "x${GRUB_HIDDEN_TIMEOUT_QUIET}" = "xtrue" ] ; then
	verbose=
      else
	verbose=" --verbose"
      fi

      if [ "x${1}" = "x0" ] ; then
	cat <<EOF
if [ "x\${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep$verbose --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
EOF
      else
	cat << EOF
if [ "x\${timeout}" != "x-1" ]; then
  if sleep$verbose --interruptible ${GRUB_HIDDEN_TIMEOUT} ; then
    set timeout=0
  fi
fi
EOF
      fi
    fi
  fi
}

adjust_timeout () {
  if [ "x$GRUB_BUTTON_CMOS_ADDRESS" != "x" ]; then
    cat <<EOF
if cmostest $GRUB_BUTTON_CMOS_ADDRESS ; then
EOF
    make_timeout "${GRUB_HIDDEN_TIMEOUT_BUTTON}" "${GRUB_TIMEOUT_BUTTON}"
    echo else
    make_timeout "${GRUB_HIDDEN_TIMEOUT}" "${GRUB_TIMEOUT}"
    echo fi
  else
    make_timeout "${GRUB_HIDDEN_TIMEOUT}" "${GRUB_TIMEOUT}"
  fi
}

if [ "x${GRUB_DISABLE_OS_PROBER}" = "xtrue" ]; then 
  adjust_timeout
  exit 0
fi

if [ -z "`which os-prober 2> /dev/null`" -o -z "`which linux-boot-prober 2> /dev/null`" ] ; then
  # missing os-prober and/or linux-boot-prober
  adjust_timeout
  exit 0
fi

OSPROBED="`os-prober | tr ' ' '^' | paste -s -d ' '`"
if [ -z "${OSPROBED}" ] ; then
  # empty os-prober output, nothing doing
  adjust_timeout
  exit 0
fi

osx_entry() {
	found_other_os=1
        cat << EOF
menuentry "${LONGNAME} (${2}-bit) (on ${DEVICE})" --class osx --class darwin --class os {
EOF
	save_default_entry | sed -e "s/^/\t/"
	prepare_grub_to_access_device ${DEVICE} | sed -e "s/^/\t/"
	cat << EOF
        load_video
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ \$do_resume = 0 ]; then
           xnu_uuid ${OSXUUID} uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           $1 /mach_kernel boot-uuid=\${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
EOF
}

wubi=

for OS in ${OSPROBED} ; do
  DEVICE="`echo ${OS} | cut -d ':' -f 1`"
  LONGNAME="`echo ${OS} | cut -d ':' -f 2 | tr '^' ' '`"
  LABEL="`echo ${OS} | cut -d ':' -f 3 | tr '^' ' '`"
  BOOT="`echo ${OS} | cut -d ':' -f 4`"

  if [ -z "${LONGNAME}" ] ; then
    LONGNAME="${LABEL}"
  fi

  echo "Found ${LONGNAME} on ${DEVICE}" >&2

  case ${BOOT} in
    chain)

      case ${LONGNAME} in
	Windows*)
	  if [ -z "$wubi" ]; then
	    if [ -x /usr/share/lupin-support/grub-mkimage ] && \
	       /usr/share/lupin-support/grub-mkimage --test; then
	      wubi=yes
	    else
	      wubi=no
	    fi
	  fi
	  if [ "$wubi" = yes ]; then
	    echo "Skipping ${LONGNAME} on Wubi system" >&2
	    continue
	  fi
	  ;;
      esac

      found_other_os=1
      cat << EOF
menuentry "${LONGNAME} (on ${DEVICE})" --class windows --class os {
EOF
      save_default_entry | sed -e "s/^/\t/"
      prepare_grub_to_access_device ${DEVICE} | sed -e "s/^/\t/"

      case ${LONGNAME} in
	Windows\ Vista*|Windows\ 7*|Windows\ Server\ 2008*)
	;;
	*)
	  cat << EOF
	drivemap -s (hd0) \${root}
EOF
	;;
      esac

      cat <<EOF
	chainloader +1
}
EOF
    ;;
    linux)
      LINUXPROBED="`linux-boot-prober ${DEVICE} 2> /dev/null | tr ' ' '^' | paste -s -d ' '`"
      prepare_boot_cache=

      for LINUX in ${LINUXPROBED} ; do
        LROOT="`echo ${LINUX} | cut -d ':' -f 1`"
        LBOOT="`echo ${LINUX} | cut -d ':' -f 2`"
        LLABEL="`echo ${LINUX} | cut -d ':' -f 3 | tr '^' ' '`"
        LKERNEL="`echo ${LINUX} | cut -d ':' -f 4`"
        LINITRD="`echo ${LINUX} | cut -d ':' -f 5`"
        LPARAMS="`echo ${LINUX} | cut -d ':' -f 6- | tr '^' ' '`"

        if [ -z "${LLABEL}" ] ; then
          LLABEL="${LONGNAME}"
        fi

	if [ "${LROOT}" != "${LBOOT}" ]; then
	  LKERNEL="${LKERNEL#/boot}"
	  LINITRD="${LINITRD#/boot}"
	fi

	if [ -z "${prepare_boot_cache}" ]; then
	  prepare_boot_cache="$(prepare_grub_to_access_device ${LBOOT} | sed -e "s/^/\t/")"
	  [ "${prepare_boot_cache}" ] || continue
	fi
	found_other_os=1
        cat << EOF
menuentry "${LLABEL} (on ${DEVICE})" --class gnu-linux --class gnu --class os {
EOF
	save_default_entry | sed -e "s/^/\t/"
	printf '%s\n' "${prepare_boot_cache}"
	cat <<  EOF
	linux ${LKERNEL} ${LPARAMS}
EOF
        if [ -n "${LINITRD}" ] ; then
          cat << EOF
	initrd ${LINITRD}
EOF
        fi
        cat << EOF
}
EOF
      done
    ;;
    macosx)
      OSXUUID="`grub-probe --target=fs_uuid --device ${DEVICE} 2> /dev/null`"
      osx_entry xnu_kernel 32
      osx_entry xnu_kernel64 64
    ;;
    hurd)
      found_other_os=1
      cat << EOF
menuentry "${LONGNAME} (on ${DEVICE})" --class hurd --class gnu --class os {
EOF
      save_default_entry | sed -e "s/^/\t/"
      prepare_grub_to_access_device ${DEVICE} | sed -e "s/^/\t/"
      grub_device="`${grub_probe} --device ${DEVICE} --target=drive`"
      mach_device="`echo "${grub_device}" | sed -e 's/(\(hd.*\),msdos\(.*\))/\1s\2/'`"
      grub_fs="`${grub_probe} --device ${DEVICE} --target=fs`"
      case "${grub_fs}" in
	*fs)	hurd_fs="${grub_fs}" ;;
	*)	hurd_fs="${grub_fs}fs" ;;
      esac
      cat << EOF
	multiboot /boot/gnumach.gz root=device:${mach_device}
	module /hurd/${hurd_fs}.static ${hurd_fs} --readonly \\
			--multiboot-command-line='\${kernel-command-line}' \\
			--host-priv-port='\${host-port}' \\
			--device-master-port='\${device-port}' \\
			--exec-server-task='\${exec-task}' -T typed '\${root}' \\
			'\$(task-create)' '\$(task-resume)'
	module /lib/ld.so.1 exec /hurd/exec '\$(exec-task=task-create)'
}
EOF
    ;;
    *)
      echo "  ${LONGNAME} is not yet supported by grub-mkconfig." >&2
    ;;
  esac
done

adjust_timeout

```

and the error says:

```

/etc/grub.d/30_os-prober: 30: /etc/grub.d/30_os-prober: keystatus: not found
sleep: opzione non valida -- "-"
Usare «sleep --help» per ulteriori informazioni.
done

```

sorry for the error message being in italian :D

says 'sleep: invalid option -- "-"  '

---

### Post by drs305 on 2012-07-09
> **Dareus said:**
> are you sure this line is correct? 
```
if sleep$verbose --interruptible 3 ; then
```

I get an error when running update-grub


	:oops:

Sorry. I simply cut and pasted so I don't know where that came from. But you are correct, it should be:
> if sleep --interruptible 3 ; then

---

### Post by Dareus on 2012-07-09
> **drs305 said:**
> :oops:

Sorry. I simply cut and pasted so I don't know where that came from. But you are correct, it should be:

I'm really puzzled...

1. I found in the same file many lines reporting the sleep$verbose thing
2. I removed $verbose but update-grub keeps reporting there's the error (same message above)
3. Removing the lines you suggested me to add let update-grub not to show any error (finally something that works as expected :P )
4. Syntax higlighting is really weird in that file (wrongly highlighted parts alternate with right ones)

In short, removing $verbose did not the trick for me

---

### Post by drs305 on 2012-07-09
> **Dareus said:**
> I'm really puzzled...
That's because I keep confusing you.

I've slowed down, called up Grub 1.99's 30_os-prober and found the problem. 

The section I quoted isn't really run in the 30_ script. It's copied to the grub.cfg file, so the CAT/EOF instructions need to be included in the paste operation. 

So the final result should look like this:

> make_timeout () {

	cat <<EOF
if [ "x\${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep$verbose --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
EOF

  	
  if [ "x${found_other_os}" = "x" ]|| [ "x${GRUB_FORCE_HIDDEN_MENU}" = "xtrue" ] ; then 


Save and update-grub.

---

### Post by Dareus on 2012-07-09
First of all let me thank you again for your help in solving my problem.

I did what you said but I still wasn't able to get the menu.

But please, take a look at my script (posted a few messages above): after the make_timeout function declaration there's the block you made me add (now updated to the latest version you suggested), but a few lines down, 12 to be precise, BANG! those lines were already there! And unfortunately didn't work... :(

---

### Post by drs305 on 2012-07-09
> **Dareus said:**
> First of all let me thank you again for your help in solving my problem.

I did what you said but I still wasn't able to get the menu.

But please, take a look at my script (posted a few messages above): after the make_timeout function declaration there's the block you made me add (now updated to the latest version you suggested), but a few lines down, 12 to be precise, BANG! those lines were already there! And unfortunately didn't work... :(

The reason it appears twice is the second is within a conditional (regarding GRUB_HIDDEN_TIMEOUT_QUIET). So we are manually forcing the timeout check into the final product, but it also may appear if conditions are met later on. By placing it at the start of the section you guarantee it's going to be in the final product (even if it may appear twice under certain conditions). Since you are forcing it to appear in the final product under any conditions, you could remove it from the conditional section, but I'd rather not.

We'll give this one more shot and if it doesn't work I'll tell you how I set it up a bit differently. I'd rather get it working this way first.

Finding mistakes in scripts can be difficult to do, especially if they have been modified multiple times. Rather, rename your current file, remove the executable bit, and then save the attached file as your /etc/grub.d/30_os-prober file. Make it executable, then update grub. I've placed the timeout check at the end of the file.

```
sudo cp /etc/grub.d/30_os-prober /etc/grub.d/30_os-prober.old
sudo chmod -x /etc/grub.d/30_os-prober.old

```
Copy the entire contents below into /etc/grub.d/30_os-prober, save the file, then
```
sudo chmod +x /etc/grub.d/30_os-prober
sudo update-grub

```

Here is the entire Grub 1.99 script
```

#! /bin/sh
set -e

# grub-mkconfig helper script.
# Copyright (C) 2006,2007,2008,2009  Free Software Foundation, Inc.
#
# GRUB is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# GRUB is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with GRUB.  If not, see <http://www.gnu.org/licenses/>.

prefix="/usr"
exec_prefix="${prefix}"
datarootdir="${prefix}/share"

. "${datarootdir}/grub/grub-mkconfig_lib"

found_other_os=

make_timeout () {
 	
  if [ "x${found_other_os}" = "x" ] || [ "x${GRUB_FORCE_HIDDEN_MENU}" = "xtrue" ] ; then 
    if [ "x${1}" != "x" ] ; then
      if [ "x${GRUB_HIDDEN_TIMEOUT_QUIET}" = "xtrue" ] ; then
	verbose=
      else
	verbose=" --verbose"
      fi

      if [ "x${1}" = "x0" ] ; then
	cat <<EOF
if [ "x\${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep$verbose --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
EOF
      else
	cat << EOF
if [ "x\${timeout}" != "x-1" ]; then
  if sleep$verbose --interruptible ${GRUB_HIDDEN_TIMEOUT} ; then
    set timeout=0
  fi
fi
EOF
      fi
    fi
  fi
}

adjust_timeout () {
  if [ "x$GRUB_BUTTON_CMOS_ADDRESS" != "x" ]; then
    cat <<EOF
if cmostest $GRUB_BUTTON_CMOS_ADDRESS ; then
EOF
    make_timeout "${GRUB_HIDDEN_TIMEOUT_BUTTON}" "${GRUB_TIMEOUT_BUTTON}"
    echo else
    make_timeout "${GRUB_HIDDEN_TIMEOUT}" "${GRUB_TIMEOUT}"
    echo fi
  else
    make_timeout "${GRUB_HIDDEN_TIMEOUT}" "${GRUB_TIMEOUT}"
  fi
}

if [ "x${GRUB_DISABLE_OS_PROBER}" = "xtrue" ]; then
  adjust_timeout
  exit 0
fi

if [ -z "`which os-prober 2> /dev/null`" -o -z "`which linux-boot-prober 2> /dev/null`" ] ; then
  # missing os-prober and/or linux-boot-prober
  adjust_timeout
  exit 0
fi

OSPROBED="`os-prober | tr ' ' '^' | paste -s -d ' '`"
if [ -z "${OSPROBED}" ] ; then
  # empty os-prober output, nothing doing
  adjust_timeout
  exit 0
fi

osx_entry() {
	found_other_os=1
        cat << EOF
menuentry "${LONGNAME} (${2}-bit) (on ${DEVICE})" --class osx --class darwin --class os {
EOF
	save_default_entry | sed -e "s/^/\t/"
	prepare_grub_to_access_device ${DEVICE} | sed -e "s/^/\t/"
	cat << EOF
        load_video
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ \$do_resume = 0 ]; then
           xnu_uuid ${OSXUUID} uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           $1 /mach_kernel boot-uuid=\${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
EOF
}

wubi=

for OS in ${OSPROBED} ; do
  DEVICE="`echo ${OS} | cut -d ':' -f 1`"
  LONGNAME="`echo ${OS} | cut -d ':' -f 2 | tr '^' ' '`"
  LABEL="`echo ${OS} | cut -d ':' -f 3 | tr '^' ' '`"
  BOOT="`echo ${OS} | cut -d ':' -f 4`"

  if [ -z "${LONGNAME}" ] ; then
    LONGNAME="${LABEL}"
  fi

  echo "Found ${LONGNAME} on ${DEVICE}" >&2

  case ${BOOT} in
    chain)

      case ${LONGNAME} in
	Windows*)
	  if [ -z "$wubi" ]; then
	    if [ -x /usr/share/lupin-support/grub-mkimage ] && \
	       /usr/share/lupin-support/grub-mkimage --test; then
	      wubi=yes
	    else
	      wubi=no
	    fi
	  fi
	  if [ "$wubi" = yes ]; then
	    echo "Skipping ${LONGNAME} on Wubi system" >&2
	    continue
	  fi
	  ;;
      esac

      found_other_os=1
      cat << EOF
menuentry "${LONGNAME} (on ${DEVICE})" --class windows --class os {
EOF
      save_default_entry | sed -e "s/^/\t/"
      prepare_grub_to_access_device ${DEVICE} | sed -e "s/^/\t/"

      case ${LONGNAME} in
	Windows\ Vista*|Windows\ 7*|Windows\ Server\ 2008*)
	;;
	*)
	  cat << EOF
	drivemap -s (hd0) \${root}
EOF
	;;
      esac

      cat <<EOF
	chainloader +1
}
EOF
    ;;
    linux)
      LINUXPROBED="`linux-boot-prober ${DEVICE} 2> /dev/null | tr ' ' '^' | paste -s -d ' '`"
      prepare_boot_cache=

      for LINUX in ${LINUXPROBED} ; do
        LROOT="`echo ${LINUX} | cut -d ':' -f 1`"
        LBOOT="`echo ${LINUX} | cut -d ':' -f 2`"
        LLABEL="`echo ${LINUX} | cut -d ':' -f 3 | tr '^' ' '`"
        LKERNEL="`echo ${LINUX} | cut -d ':' -f 4`"
        LINITRD="`echo ${LINUX} | cut -d ':' -f 5`"
        LPARAMS="`echo ${LINUX} | cut -d ':' -f 6- | tr '^' ' '`"

        if [ -z "${LLABEL}" ] ; then
          LLABEL="${LONGNAME}"
        fi

	if [ "${LROOT}" != "${LBOOT}" ]; then
	  LKERNEL="${LKERNEL#/boot}"
	  LINITRD="${LINITRD#/boot}"
	fi

	if [ -z "${prepare_boot_cache}" ]; then
	  prepare_boot_cache="$(prepare_grub_to_access_device ${LBOOT} | sed -e "s/^/\t/")"
	  [ "${prepare_boot_cache}" ] || continue
	fi
	found_other_os=1
        cat << EOF
menuentry "${LLABEL} (on ${DEVICE})" --class gnu-linux --class gnu --class os {
EOF
	save_default_entry | sed -e "s/^/\t/"
	printf '%s\n' "${prepare_boot_cache}"
	cat <<  EOF
	linux ${LKERNEL} ${LPARAMS}
EOF
        if [ -n "${LINITRD}" ] ; then
          cat << EOF
	initrd ${LINITRD}
EOF
        fi
        cat << EOF
}
EOF
      done
    ;;
    macosx)
      OSXUUID="`grub-probe --target=fs_uuid --device ${DEVICE} 2> /dev/null`"
      osx_entry xnu_kernel 32
      osx_entry xnu_kernel64 64
    ;;
    hurd)
      found_other_os=1
      cat << EOF
menuentry "${LONGNAME} (on ${DEVICE})" --class hurd --class gnu --class os {
EOF
      save_default_entry | sed -e "s/^/\t/"
      prepare_grub_to_access_device ${DEVICE} | sed -e "s/^/\t/"
      grub_device="`${grub_probe} --device ${DEVICE} --target=drive`"
      mach_device="`echo "${grub_device}" | sed -e 's/(\(hd.*\),msdos\(.*\))/\1s\2/'`"
      grub_fs="`${grub_probe} --device ${DEVICE} --target=fs`"
      case "${grub_fs}" in
	*fs)	hurd_fs="${grub_fs}" ;;
	*)	hurd_fs="${grub_fs}fs" ;;
      esac
      cat << EOF
	multiboot /boot/gnumach.gz root=device:${mach_device}
	module /hurd/${hurd_fs}.static ${hurd_fs} --readonly \\
			--multiboot-command-line='\${kernel-command-line}' \\
			--host-priv-port='\${host-port}' \\
			--device-master-port='\${device-port}' \\
			--exec-server-task='\${exec-task}' -T typed '\${root}' \\
			'\$(task-create)' '\$(task-resume)'
	module /lib/ld.so.1 exec /hurd/exec '\$(exec-task=task-create)'
}
EOF
    ;;
    *)
      echo "  ${LONGNAME} is not yet supported by grub-mkconfig." >&2
    ;;
  esac
done

adjust_timeout


	cat <<EOF
if [ "x\${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep$verbose --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
EOF

```
Save the file and update-grub.

---

### Post by Dareus on 2012-07-09
YAY! Thank you it worked! Thank you very much!

I'm still not getting exactly what was wrong, with diff I didn't see anything strange. I think it was mostly about all those nested conditional switches

---

### Post by drs305 on 2012-07-09
> **Dareus said:**
> YAY! Thank you it worked! Thank you very much!

Now for the rest of the story...

Rather than put the keystatus check at the end of 30..., I keep a copy in /etc/grub.d/40_custom. The reason is that if the GRUB package is updated the 30_os-prober file may change as well and you will lose the keystatus check. Of course, you will also lose the additional modification, but being able to stop the boot is much more important for me. I can always re-apply other modifications after booting.

So I don't have the extra keystatus check in 30, but in 40_custom. The only difference is that you don't include the CAT/EOF lines in the custom file, since it's assumed everything below the intro lines is to be imported. GRUB package updates won't alter your 40_custom file without asking you. Even more safe, you could make a 50_custom file since that one doesn't exist in Grub and would never be touched by Grub.

---

### Post by Dareus on 2012-07-09
Ok, I'd try what you suggest because "Best practices" means something :)

I actually have two things to look into to have the boot-experience I'm trying to achieve. 
The fist one is to set a splash image to show during the ```
GRUB_HIDDEN_TIMEOUT
``` phase.
The second one is that I wonder if it is possible to show the menu pressing any key, not just the SHIFT key.

About the splash image I already took the image (RGB non-indexed) and 640x480, put it in ```
/boot/grub
``` and have it recognized from ```
update-grub
``` but it doesn't show up. I was wondering if there's a way to know which is the resolution GRUB2 is actually running at; I like how it looks and I'm not interested in modifying it, so I'm not very interested in what are the supported resolution other than that.

---

### Post by drs305 on 2012-07-09
> **Dareus said:**
> 
About the splash image I already took the image (RGB non-indexed) and 640x480, put it in ```
/boot/grub
``` and have it recognized from ```
update-grub
``` but it doesn't show up. I was wondering if there's a way to know which is the resolution GRUB2 is actually running at; I like how it looks and I'm not interested in modifying it, so I'm not very interested in what are the supported resolution other than that.
I'll tackle this one first since it's the easier of the two questions.
During boot, if you display the menu and then press 'c' you will get to the Grub prompt. Type "vbeinfo" and it will show the resolutions available to Grub. At the bottom of the screen should be a "Preferred mode" which is the resolution being used if you haven't manually selected one in /etc/default/grub.

You can force Grub to use a supported resolution in /etc/default/grub's GRUB_GFXMODE= setting. Just remove the # symbol and use a supported resolution.

> **Dareus said:**
> 
I actually have two things to look into to have the boot-experience I'm trying to achieve. 
The fist one is to set a splash image to show during the ```
GRUB_HIDDEN_TIMEOUT
``` phase.
The second one is that I wonder if it is possible to show the menu pressing any key, not just the SHIFT key.

I'll have to get back to you on this one. There was once documentation from the GNU GRUB folks that indicated the GRUB splash image should show as the hidden timeout counted down. The results were very sporadic but I haven't tried it lately. I'll experiment and see what happens and post when I have something. There is a very convoluted workaround I came up with originally but hopefully I won't have to go there again.

The countdown should also stop with the ESC key, and I've had some systems that stop the countdown when any key is pressed. I'll look at this again as well.

---

### Post by drs305 on 2012-07-09
Here is part 2 of the answer - well, part 2 of the question, as I'm not sure I have the answer...

To show the splash only (no menu) during a timeout:
In /etc/default/grub:
```
GRUB_HIDDEN_TIMEOUT=15  # No menu for given time, splash only *
GRUB_HIDDEN_TIMEOUT_QUIET=true  # or false, either way
GRUB_TIMEOUT=10 # Once displayed, 10 seconds later it will boot.
```

In /etc/grub.d/30_os-prober:
If you still have the previous hack you shouldn't have to do anything;
or Line 29:
>   if [ **[COLOR="Red"]![/COLOR]** "x${found_other_os}" = "x" ] ; then
or Line 29:
> if [ "x${found_other_os}" = "x" ] || [ "x${GRUB_COUNTER}" = "xtrue" ] ; then
WITH this in /etc/default/grub
> GRUB_COUNTER="true"
export GRUB_COUNTER

Now the rub. On my machine, the system will be completely blank until I press any key once. This should not be necessary. At that time on my machine the boot splash image appears and the system counts down until the hidden timeout expires or the ESC or SHIFT key is pressed.

The 'any key' works to display the splash key on my machine, but only the ESC or SHIFT key reveal the menu. I don't know how to get the 'any key' effect you seek.

The extra key press necessary on my machine pretty much negates the effect you want IMO. Perhaps it's a quirk on my machine and the preliminary key press isn't necessary for anyone else.

---

### Post by Redsandro on 2012-07-10
-edit-

My mistake. I didn't see 2 pages of replies.

---

### Post by Redsandro on 2012-07-10
My original post for archival purposes since I accidentally the whole post anyway:

> **Dareus said:**
> Just BUMPING Redsandro's request ;P

Actually it works for me now. I remember vividly that both methods did not work so I cannot remember what changed or needed to change.

But in the end I used point **11 method 2** as described by **drs305**, and for practical purposes in case I changed the config, here's my **/etc/default/grub**:
```
# If you change this file, run 'update-grub' afterwards to update.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_TIMEOUT=3
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# RED FIX hold control for menu?
GRUB_FORCE_HIDDEN_MENU="true"
export GRUB_FORCE_HIDDEN_MENU

```

---

### Post by Dareus on 2012-07-10
> **drs305 said:**
> I'll tackle this one first since it's the easier of the two questions.
During boot, if you display the menu and then press 'c' you will get to the Grub prompt. Type "vbeinfo" and it will show the resolutions available to Grub. At the bottom of the screen should be a "Preferred mode" which is the resolution being used if you haven't manually selected one in /etc/default/grub.

You can force Grub to use a supported resolution in /etc/default/grub's GRUB_GFXMODE= setting. Just remove the # symbol and use a supported resolution.

Ok, thank you! I found out GRUB was running at a higher resolutions than what I was expecting.

> **drs305 said:**
> Here is part 2 of the answer - well, part 2 of the question, as I'm not sure I have the answer...

To show the splash only (no menu) during a timeout:
In /etc/default/grub:
```
GRUB_HIDDEN_TIMEOUT=15  # No menu for given time, splash only *
GRUB_HIDDEN_TIMEOUT_QUIET=true  # or false, either way
GRUB_TIMEOUT=10 # Once displayed, 10 seconds later it will boot.
```


Not that I don't believe you, which would be impossible now :D , but why show I change those values? I have 

```
GRUB_HIDDEN_TIMEOUT=5  
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=0 
```

Somewhere (I suppose on the community doc) I read that after GRUB_HIDDEN_TIMEOUT seconds, the menu is shown for GRUB_TIMEOUT seconds; so I'd better keep the latter to 0. :confused:
Please correct me if I'm wrong

> **drs305 said:**
> 
In /etc/grub.d/30_os-prober:
If you still have the previous hack you shouldn't have to do anything;
or Line 29:
[QUOTE=drs305;12089121]
if [ ! "x${found_other_os}" = "x" ] ; then 

or Line 29:
> **drs305 said:**
> 
if [ "x${found_other_os}" = "x" ] || [ "x${GRUB_COUNTER}" = "xtrue" ] ; then 

WITH this in /etc/default/grub
> **drs305 said:**
> 
GRUB_COUNTER="true"
export GRUB_COUNTER 

[/QUOTE]

I changed the script you provided me to move the last few lines to a custom script. This way line 29 should already be like that but it isn't actually (to be honest *if [ ! "x${found_other_os}" = "x" ] ; then* appears on line 30). I suppose I have to change that as you suggested.

> **drs305 said:**
> Now the rub. On my machine, the system will be completely blank until I press any key once. This should not be necessary. At that time on my machine the boot splash image appears and the system counts down until the hidden timeout expires or the ESC or SHIFT key is pressed.

The 'any key' works to display the splash key on my machine, but only the ESC or SHIFT key reveal the menu. I don't know how to get the 'any key' effect you seek.

The extra key press necessary on my machine pretty much negates the effect you want IMO. Perhaps it's a quirk on my machine and the preliminary key press isn't necessary for anyone else.

I read about this behaviour earlier, so I suppose you're not the only one with this issue. I tried pressing the ESC key to reveal the menu, but it didn't work, only SHIFT works reliably.

---

### Post by drs305 on 2012-07-10
You would leave the GRUB_TIMEOUT at 0 for no menu display. I use a value for troubleshooting purposes only. Even then, I normally keep a value of 1 so I can always interrupt the boot. But that would negate your desire, if only for a second.

I'm on a business trip and when I have time I've been playing with custom menus which would act the way GRUB should work (without having to press a key to display the timeout splash screen). If I come up with something I'll post.

---

### Post by drs305 on 2012-07-11
After much experimenting I think I found a way to display the splash menu without having to press a key first, and then displaying with the SHIFT or ESC key (any other key displays the countdown time remaining). 

Dareus, if you are still interested let me know and I'll purge/reinstall GRUB so I know I'm working with the default scripts and not my variations. I'll try to figure out a script modification rather than a straight hack of the grub.cfg file so it can be done automatically. 

It's been a giant puzzle but I won't pursue it unless someone wants to use this functionality.

---

### Post by Dareus on 2012-07-11
> **drs305 said:**
> After much experimenting I think I found a way to display the splash menu without having to press a key first, and then displaying with the SHIFT or ESC key (any other key displays the countdown time remaining). 

Dareus, if you are still interested let me know and I'll purge/reinstall GRUB so I know I'm working with the default scripts and not my variations. I'll try to figure out a script modification rather than a straight hack of the grub.cfg file so it can be done automatically. 

It's been a giant puzzle but I won't pursue it unless someone wants to use this functionality.

Absolutely, I'm still interested and many others are, too! I found many people on the internet asking how to do that!

Still, I can't tell you "thank you" enough

---

### Post by drs305 on 2012-07-11
> **Dareus said:**
> Absolutely, I'm still interested and many others are, too! I found many people on the internet asking how to do that!

Ok. Deep breath - I don't know how much I'll relate as to my tests or how much detail I'll go into here. The disclaimer is that this works on two of my machines - it probably will work on yours but there could be differences. Also - this post deals with the GRUB splash image and doesn't address/solve the blank screen after GRUB passes control and before unity-greeter/pymouth displays it's splash screen.

I started by purging and reinstalling Grub so I was working with a fresh version of Grub 1.99. You don't need to do this, but I haven't tried to incorporate it with what we have already done.

**Overview: **
1. The following should allow the system to boot to a splash screen. The screen should appear without the necessity of pressing any key. A welcome message can be included on the splash screen if desired (with an annoying cursor underneath, which I haven't figured out how to hide). Of course, you could also include a welcome message embedded on the screen by editing the image with a graphics program. The timeout counter won't be displayed for some reason (although there is a workaround method not discussed here).

2. Pressing either the SHIFT or ESC key will display the menu (if GRUB_TIMEOUT is greater than 0, or boot immediately if it is 0. If the menu is displayed, it will boot after the GRUB_TIMEOUT value. Pressing the key again if the menu is displayed will stop the counter.

3. Pressing any other key will display the time remaining until the system automatically boots or displays the menu.

**Setup:**

Create a custom script. I've called it 06_splash. The name should start with "06" so it is placed in grub.cfg after the 05_debian_theme script but before the menuentries.

```
sudo touch /etc/grub.d/06_splash
sudo chmod +x /etc/grub.d/06_splash
gksu gedit /etc/grub.d/06_splash /etc/default/grub
```

[B]
In /etc/default/grub, set these values:[/B]
GRUB_TIMEOUT  # 0 for automatic booting without ever seeing the menu or the number of seconds to wait *after it displays* before booting.
GRUB_HIDDEN_TIMEOUT # Seconds to press SHIFT or ESC before the menu displays or system boots.
GRUB_BACKGROUND # Optional. Place a graphic image in /boot/grub or designate an image here (GRUB_BACKGROUND=/path/imagename.png)
Samples:
> 
GRUB_TIMEOUT=0  # I use a small positive value during testing so I know when the transfer occurs and I can stop it if necessary.
GRUB_HIDDEN_TIMEOUT=10 # Use an odd number such as 23 if you plan on reviewing what happens in grub.cfg.  Doing a search for 23 is much easier than a search for 10. Set to desired value once you know it works.
GRUB_BACKGROUND=/images/mygrubimage.png # Or just put the image in /boot/grub and this line isn't necessary. If you use this line, remove images from /boot/grub folder.


**Content:**
The script is pretty straightforward. It took me dozens of boots to come up with the following for a variety of reasons - mostly because I'm not a scripter/programmer. There are probably better ways of doing things, but here is what I came up with. Paste the contents into the script.

> 
#!/bin/sh
echo 1>&2 "Adding 06_splash"

cat << EOF
# This file allows a GRUB 2 splash screen to appear w/o keystrokes.
# Press the ESC or SHIFT key to display the GRUB menu.
# If no action is taken, the menu will display for GRUB_TIMEOUT before booting.
EOF

# Make sure no recordfail event has occurred, then run the script.
cat << EOF
if [ "x\${timeout}" != "x-1" ]; then

# GRUB colors available in the menu:  color1/color2
# black, blue, brown, cyan, dark-gray, green, light-cyan, light-blue, light-green,
# light-gray, light-magenta, light-red, magenta, red, white, yellow
# /black is transparency code for second value
# Samples text/background combinations
# menu_color_normal=light-gray/dark-gray
# menu_color_highlight=yellow/dark-gray
# color_normal=light-gray/dark-gray

# Display splash background. If no welcome message, comment the 'echo' line.
clear
echo "Welcome to Ubuntu - Press the ESC or SHIFT Key to Continue"
sleep --verbose --interruptible $GRUB_HIDDEN_TIMEOUT
fi
EOF

cat << EOF
# Determine if the user interrupted the splash countdown, then boot or display the menu.
if [ \$? = "0" ]; then
set timeout=$GRUB_TIMEOUT
else
set timeout=-1
fi
EOF


Save the file and update-grub.

NOTE: Rather than edit GRUB's 'official' scripts, this script places information after the 00_header and 05_debian_theme inputs. Some of these may duplicate entries in the previous sections of grub.cfg, but since they come later they will be used. Additionally, this script will not be changed if 00 or 05 is updated via a GRUB package update.

**Explanations and elaborations:**
> echo 1>&2 "Adding 06_splash" 
Not required; it shows the script being added in the terminal output when update-grub is run.

> cat << EOF
Copies input to grub.cfg until "EOF" marker is found.

> Comments
The colors listed in the remarks are the ones recognized by GRUB. You can use them for the menu text, highlight bars, etc. Black used as the second value is treated as "transparent". More on that later (maybe).

> if [ "x\${timeout}" != "x-1" ]; then
The remainder will take effect if the timeout is -1. This value means the menu will display and await user input. The most common way the value becomes -1 is after a failed boot. The \ is necessary for proper importation when using 'cat'

> 
#	menu_color_normal=light-gray/dark-gray	
#	menu_color_highlight=yellow/dark-gray	
#	color_normal=light-gray/dark-gray
These values set the text (and background) colors. You don't need these unless the automatic text color selection isn't working with your image or you want something different. I may elaborate on these later, but the *color_normal* would be the color of the Welcome message and the text outside the menu borders. Additionally, if you are not using a background image you can set the text and solid background colors (except a black background) by using these settings.

The *menu_color_highlight* are the colors of the highlighted menuentry and the color of the background bar.

The *menu_color_normal* is the text color of the non-selected menu item and the background color.

Remember /black means 'transparent' - i.e. you will see the background image. The available colors are in the script comments. See the links at the end of this post for some links with fuller explanations.


> clear
It took me a long time, and many variations, before I stumbled on this line. This is the command which will display the background image automatically without having to press a key.

> echo "Welcome to Ubuntu - Press the ESC or SHIFT Key to Continue"

Optional. You'll have the annoying _ underneath it. You could embed your message in your graphic as an alternative. If you want to change the message color, uncomment the "color_normal" setting above and choose your color. The second color should be /black if you are using a background image. If you don't want a message, comment (#) the line or remove it completely.

> sleep --verbose --interruptible $GRUB_HIDDEN_TIMEOUT
This will import the /etc/default/grub GRUB_HIDDEN_TIMEOUT value. The menu will remain hidden for this many seconds, then either boot or display based on the GRUB_TIMEOUT setting. Even though it's verbose and should display the timer, it doesn't for me when using a graphic. NOTE: The switches are preceded by two - , it's not a single long dash.

> if [ \$? = "0" ]; then
Another line that took me way longer than it should have to figure out. It is a conditional which determines whether you have pressed a key to interrupt the hidden timeout countdown.

> set timeout=$GRUB_TIMEOUT
else
set timeout=-1
If you don't press any key, it will immediately boot if GRUB_TIMEOUT is 0 or display the menu for GRUB_TIMEOUT seconds. If you do press the SHIFT or ESC key during the countdown, the menu will display. At that point, the menu will display for the GRUB_TIMEOUT number of seconds before booting. If it is set at 0, you will not see the menu before it boots.

**A bit about the menu colors**
If you don't include a background image, you can use the commented section (by uncommenting one or more) to set the background color.

If the second value is /black, your image will appear behind the menu. If the second value is an approved color, it will be opaque.

If you leave them commented and don't use an image, I believe Ubuntu is going to use the purple/aubergine background. 

One final note about solid colors. I like clean black backgrounds but it's a bit tricky in Grub. Since the background color is designated by /xxxxxx, but /black is used as "transparency", I don't think you can set it with the color designations. What I did to achieve a black screen with a small image on it was to create a solid black image and used that as my background.

As I was testing there were all sorts of things I thought I could relate, but the ones above are the major ones.

Don't forget to update-grub for the changes to take affect.

I've written a couple of tutorials and ubuntu.help pages that might help if you don't understand the color selections:

[_https://help.ubuntu.com/community/Grub2/Displays_]("https://help.ubuntu.com/community/Grub2/Displays")

[_Grub 2 Drop-In Backgrounds & Font Selection_]("http://ubuntuforums.org/showthread.php?t=1739412")

---

### Post by Dareus on 2012-07-12
Tank you so much! Everything works fine now! It would have been impossible without your help! Again, thank you!

---

### Post by skellobissis on 2012-07-26
What i essentially want to accomplish is to hide my ubuntu install and have the system automatically boot to windows 7. 

I can make it boot to windows 7 automatically, that was simple.  

I followed each different way of hiding the bootloader screen on section 11 but when i do and update grub, the windows 7 option is not available.  

how can i set this up to automatically boot to windows 7, and hide the boot loader prompt, but allow me to hit shift to access the bootloader screen?

Thanks, 

-Tony

---

### Post by drs305 on 2012-07-26
#235
skellobissis,

Welcome to the Ubuntu Forums.

I'd probably have to see the contents of RESULTS.txt to see what is happening with your system but an easier option for you may be to try Grub Customizer. It probably has a way of doing what you wish. (See BIS and Customizer links in my sig line)

If it can't do what you want just post back and we can probably add something to a custom file to make sure the SHIFT option is available.

---

