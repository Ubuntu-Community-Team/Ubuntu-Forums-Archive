---
title: "How to add a menuentry to 'Advanced options' of grub regeneration script"
date: 2016-08-26
forum: Tutorials
---

### Post by Jimysbil on 2016-08-26
I have seen a lot of people asking questions about grub and they are wondering if they would be able to do some specific things with it.Grub is the most popular bootloader and it's being used in a lot of distributions (Ubuntu , Mint , Debian e.t.c.).
After a lot google search about adding an option to the 'Advanced options' submenu of grub regeneration script, I wasn't be able to find anything to help me out.So I desided to make some changes by myself in order to make it work.

[SIZE=2][I][B][COLOR=#ff0000]** This guide is tested on Ubuntu and Kali linux but you shouldn't have problem to use it on other distributions. **
*  This tutorial is made for grub 2.02~beta2-36 scripts  *[/COLOR][/B][/I][/SIZE]

_**STEP 1**_

Open a terminal and type the command:
```
sudo su
```

(type the password when it's being asked)
* It will give you root permissions.Everything you are doing from now on is up to you *

_**STEP 2**_

[COLOR=#ff0000]**_* After you have succesfully get root permissions you should better take a backup of your scripts before you edit them, just in case you mess it up and you don't remember how to revert the changes by yourself. *_**[/COLOR]

You have to backup _*/usr/sbin/grub-mkconfig*_ _*/etc/default/grub*_ files and _*/etc/grub.d/*_ folder because we are going to edit their contents.(You should probably make a backup of your *_/boot/grub/grub.cfg_* file just in case your system stays unbootable after the procedure.)

So type those commands to the terminal:
```
cp /usr/sbin/grub-mkconfig /usr/sbin/grub-mkconfig.backup
cp /etc/default/grub /etc/default/grub.backup
cp -r /etc/grub.d /etc/grub.d.backup
cp /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
```

[COLOR=#ff0000]_**If you get an error message don't proceed unless you know what you are doing.**_[/COLOR]

**_STEP 3_**

As long as you have your backup you are ready to start the editing proccess.

Give the command:
```
gedit /usr/sbin/grub-mkconfig /etc/default/grub /etc/grub.d/10_linux
```

Now you should be able to see the three scripts you need to edit on 'gedit' text editor.

_**STEP 4**_

So the first thing you have to do is to manually patch the _*grub-mkconfig*_ script by adding some new variables.

Go to _*grub-mkconfig*_ tab and search the script untill you find:
```
# These are optional, user-defined variables.
```

Add a line for eash of these new variables:
```
GRUB_CMDLINE_LINUX_OPTION1 \
GRUB_DISABLE_OPTION1 \
GRUB_OPTION1_TITLE \
```

[SIZE=2]***Example:***[/SIZE]
```
# These are optional, user-defined variables.
export GRUB_DEFAULT \
  GRUB_HIDDEN_TIMEOUT \
  GRUB_HIDDEN_TIMEOUT_QUIET \
  GRUB_TIMEOUT \
  GRUB_TIMEOUT_STYLE \
  GRUB_DEFAULT_BUTTON \
  GRUB_HIDDEN_TIMEOUT_BUTTON \
  GRUB_TIMEOUT_BUTTON \
  GRUB_TIMEOUT_STYLE_BUTTON \
  GRUB_BUTTON_CMOS_ADDRESS \
  GRUB_BUTTON_CMOS_CLEAN \
  GRUB_DISTRIBUTOR \
  GRUB_CMDLINE_LINUX \
  GRUB_CMDLINE_LINUX_DEFAULT \
  GRUB_CMDLINE_LINUX_OPTION1 \
  GRUB_CMDLINE_XEN \
  GRUB_CMDLINE_XEN_DEFAULT \
  GRUB_CMDLINE_LINUX_XEN_REPLACE \
  GRUB_CMDLINE_LINUX_XEN_REPLACE_DEFAULT \
  GRUB_CMDLINE_NETBSD \
  GRUB_CMDLINE_NETBSD_DEFAULT \
  GRUB_CMDLINE_GNUMACH \
  GRUB_TERMINAL_INPUT \
  GRUB_TERMINAL_OUTPUT \
  GRUB_SERIAL_COMMAND \
  GRUB_DISABLE_LINUX_UUID \
  GRUB_DISABLE_RECOVERY \
  GRUB_DISABLE_OPTION1 \
  GRUB_VIDEO_BACKEND \
  GRUB_GFXMODE \
  GRUB_BACKGROUND \
  GRUB_THEME \
  GRUB_GFXPAYLOAD_LINUX \
  GRUB_DISABLE_OS_PROBER \
  GRUB_INIT_TUNE \
  GRUB_SAVEDEFAULT \
  GRUB_ENABLE_CRYPTODISK \
  GRUB_BADRAM \
  GRUB_OS_PROBER_SKIP_LIST \
  GRUB_DISABLE_SUBMENU \
  GRUB_RECORDFAIL_TIMEOUT \
  GRUB_RECOVERY_TITLE \
  GRUB_OPTION1_TITLE
```

***[COLOR=#ff0000]** The last line should not have a (\)[/COLOR]***

Somewhere inside the script you should see:
```
if [ "x${GRUB_RECOVERY_TITLE}" = "x" ]; then
  GRUB_RECOVERY_TITLE="recovery mode"
fi
```

Let a blank line and add:
```
if [ "x${GRUB_OPTION1_TITLE}" = "x" ]; then
  GRUB_OPTION1_TITLE="my special mode"
fi
```

As long as you make the changes save them.

_**STEP 5**_

Go to *_10_linux_ tab*.You should be able to find somewhere:
  ```
if [ "x${GRUB_DISABLE_RECOVERY}" != "xtrue" ]; then
    linux_entry "${OS}" "${version}" recovery \
                "${GRUB_CMDLINE_LINUX_RECOVERY} ${GRUB_CMDLINE_LINUX}"
  fi
```

Let a blank line and add:
  ```
if [ "x${GRUB_DISABLE_OPTION1}" != "xtrue" ]; then
    linux_entry "${OS}" "${version}" option1 \
                "${GRUB_CMDLINE_LINUX} ${GRUB_CMDLINE_LINUX_OPTION1}"
  fi
```

You should also be able to find:
      ```
recovery)
          title="$(gettext_printf "%s, with Linux %s (%s)" "${os}" "${version}" "$(gettext "${GRUB_RECOVERY_TITLE}")")" ;;
```

press enter at the end of this line and add:
      ```
option1)
          title="$(gettext_printf "%s, with Linux %s (%s)" "${os}" "${version}" "$(gettext "${GRUB_OPTION1_TITLE}")")" ;;
```

It should look like this:
 ```
if [ x$type != xsimple ] ; then
      case $type in
      recovery)
          title="$(gettext_printf "%s, with Linux %s (%s)" "${os}" "${version}" "$(gettext "${GRUB_RECOVERY_TITLE}")")" ;;
      vesa)
          title="$(gettext_printf "%s, with Linux %s (%s)" "${os}" "${version}" "$(gettext "${GRUB_OPTION1_TITLE}")")" ;;
      init-*)
          title="$(gettext_printf "%s, with Linux %s (%s)" "${os}" "${version}" "${type#init-}")" ;;
      *)
          title="$(gettext_printf "%s, with Linux %s" "${os}" "${version}")" ;;
```

As long as you make the changes save them too.

_**STEP 6**_

 Now you can move to *_grub_* tab and set up everything you like.
If you want to add some specific feature to your new option you can add a new line like this:
```
GRUB_CMDLINE_LINUX_OPTION1=""
```
in order to add those options to the kernel(s) line every time the system or you execute the command 'update-grub'

For example if you want to force vesa driver on startup add:
```
GRUB_CMDLINE_LINUX_OPTION1="nomodeset xforcevesa"
```
Those options should disable nouveau driver and force vesa driver to load on your OS startup. 

You could also add:
```
GRUB_DISABLE_OPTION1="true"
```
in case you want to disable this (new) feature you just added to your script.

As long as you have make all the changes you like save them and close the application.

_**STEP 7**_
So the only thing you have to do now is to execute the command:
```
update-grub
```

This command will regenerate the *_grub.cfg_* (configuration) file for grub (bootloader) and it should have now the extra choice of yours for every kernel of your linux OS.

*[SIZE=3]**[COLOR=#ff0000]# If you face some error on the execution of the command 'update-grub' you have probably mess up with your scripts or your scripts version do not c&#959;operate well with the injected code.DON't panic!!!Just run the commands:[/COLOR]**[/SIZE]*

```
cp -f /usr/sbin/grub-mkconfig.backup /usr/sbin/grub-mkconfig
cp -f /etc/default/grub.backup /etc/default/grub
cp -rf /etc/grub.d.backup /etc/grub.d
```

* Those commands will restore your backups

Now execute the command:

```
update-grub
```

This time if all have gone well with the restoration of your backups, your grub configuration file should be regenerated without errors.

**_STEP 8_**

If you have some experience and you want to test your regenerated configuration file before you reboot your system give the command:

```
gedit /boot/grub/grub.cfg
```

_**STEP 9**_

In case you what to reboot your system immediately type:
```
reboot
```
In order to exit the root cell type:
```
exit
```

_**STEP 10**_

If you rebooted your system and everything is OK you can remove your backups safely typing:
```
sudo su
rm -f /usr/sbin/grub-mkconfig.backup
rm -f /etc/default/grub.backup
rm -rf /etc/grub.d.backup
rm -f /boot/grub/grub.cfg.backup
```

**[COLOR=#FF0000]*** [SIZE=3]Very important:[/SIZE] The rm command will delete the specific files and folders for the paths you choose.As long as you have to execute this command with root previlages make sure you will choose the specific paths either you could completely destroy your OS or even worst you could delete important files and folders.[/COLOR]**

**_STEP 11_**

In case your system is unbootable because you accidentally made something wrong with your modifications but your grub.cfg file was created without errors DON'T panic.You can always revert your untached configurations back in place.
Boot from a live CD/USB e.t.c. and open a terminal.
Type the command:
```
sudo su
```
in order to take root permissions.
Open a file explorer (nautilus for example) and mount the partition with your OS.
Go to your terminal, type 'cd' and press space.
Go to your file explorer and drag & drop the path of your mounted partition inside your terminal.

***Example:***
```
cd '/media/root/sda1'
```
* Your path will be different.This is just an example.
After that execute the commands:
```
cp -f usr/sbin/grub-mkconfig.backup usr/sbin/grub-mkconfig
cp -f etc/default/grub.backup etc/default/grub
cp -rf etc/grub.d.backup etc/grub.d
cp -f boot/grub/grub.cfg.backup boot/grub/grub.cfg
```
Those commands should restore your system in bootable condition.But in order to make sure your scripts are working well you should reboot into your OS.
Open a terminal and run the commands:
```
sudo su
update-grub
```
If everything was well, your OS should be bootable again on the next startup.

**[SIZE=3]*[COLOR=#FF0000]## When you make sure your system is bootable you can execute STEP 10.[/COLOR]*[/SIZE]**

[I][B]Congratulations!If you made all of those steps correctly you should have a working script.
If you face some problem or you need some help with it, I would be glad to help you.[/B][/I]

---

