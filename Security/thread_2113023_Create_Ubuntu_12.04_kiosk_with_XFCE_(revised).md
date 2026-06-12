---
title: "Create Ubuntu 12.04 kiosk with XFCE (revised)"
date: 2013-02-06
forum: Security
---

### Post by Charles-2007 on 2013-02-06
Create a Linux Kiosk with XFCE and Xubuntu
Version 2, February 2013
Ubuntu User Charles-2007

Objective:  a freestanding, hardened PC that connects only to whitelisted web sites (for example, as an OPAC “card catalog” station in a library).  Disclaimer:  this is less of a HOWTO and more of a “how I baked cookies using simple, plain ingredients.”

+Note:  when finished setting up the station, remember to password the BIOS and perhaps disable peripherals (CD drives) from the BIOS as added security.  Back up the installation either to a separate partition on the hard drive or to a USB flash drive (even better) using Clonezilla or equivalent.

+The following assumes a clean install on an empty drive.  Prior to installation, optionally use GParted to partition the hard drive (to create a partition to serve as a backup or for alternative use).

+Install Xubuntu 12.04 (Ubuntu with the XFCE desktop) using the default parameters.  I attempted this with 12.10 and found it too challenging.  The 12.04 will be supported until April 2017 and runs all that is below well.  This release runs XFCE 4.8.  I did try an installation of the next XFCE release on 12.04 which crashed.

+The default install choice creates a partition for the operating system, a partition for swap files, and installs GRUB the bootloader on the MBR.  Opt to get third-party files during the installation.  Encrypt the admin’s home folder for added security.  Do not select to autologin the admin.

+After installation completes, go to Ubuntu Software Center > Edit > Software Sources and under Other Sources opt for both Partners and Independent to be able to get some familiar software later.  Allow the system to download and install all the updates.  Later, when all setups are complete, I turned off automatic updates so users would not face update messages.  The admin will need to run updates periodically.

+At this point, if you have an Nvidia or ATI graphics card, the Jockey program may offer to install proprietary drivers rather than the open-source ones.  This can also be found under Settings > Additional Drivers.  This is important as without good video your web browser may slow noticeably.

+Uninstall programs (via Software Center) that are not important for your mission.  I took down messaging programs (including Thunderbird) and the like.  If unclear, leave it.  I also removed the default word processor, AbiWord, and spreadsheet Gnumeric; I installed full LibreOffice instead for our librarians (LibreOffice is perhaps more familiar to smart phone users).  I also replaced PDF viewers with Adobe Reader.  Open JDK and its plug-ins may be added if there are sites of interest that use Java.  I suggest opting for the Chromium browser rather than the default Firefox as the former is easier to control (info at the end of this article).

+XFCE uses Thunar as its file manager, Leafpad as its text editor, and Catfish as its file search program.  Shortcutting to these via the terminal (SUPER-T keys) and running them (e.g. sudo thunar) and opting to see hidden files is handy subsequently.

+Xubuntu 12.04 (and other flavors of 12.04) install a guest session by default.  Logging in as “guest” is non-persistent, meaning once logged off all the manipulations done by the guest vanish.  This seems like a good idea for a kiosk, but since this guest is allowed full run of the house (try it!), it can be deleted if desired as follows:
From the terminal:  sudo leafpad /etc/lightdm/lightdm.conf
In the Leafpad window, add the line:  allow-guest=false

+Instead of guest, I created another user (“visitor” in this example) in System > Users and Groups.  Under that user in Advanced, I disabled all options except network access.  I also created a group and added the user to it (if you want multiple users, you can then apply settings across them using groups).  This user becomes the default login as follows from the terminal:
sudo leafpad /etc/lightdm/lightdm.conf
In the Leafpad window, add:
autologin-user=visitor
autologin-user-timeout=0

With this as default, the admin can at any time log out of the user and then into an admin session.  An admin should be reminded to log out or shut down when leaving!  Log in once as the user to check it but don’t edit settings under that user for now and return to the admin.

+Note that at the loginscreen, the user sees a choice of a xubuntu or XFCE session.  To limit to just a Xubuntu session, in terminal type cd /usr/share/xsessions and then sudo rm xfce.desktop and the choice will go away.

+Perform the following steps during an admin login.  The admin panel and desktop will become the template for the user(s) later using XFCE settings.

+The bottom XFCE panel may be a distraction and can be deleted via right click options when on the panel (it is panel2).  Multiple desktops via Settings > Workspaces can be reduced to one and then it can be removed from the top panel.  For a kiosk, I suggest that the top panel should have as few items as possible.  Right click on the panel and opt for Preferences > Items and customize.
-menu showing all applications can be offered but perhaps not, or severely redacted (more on this later)
-windows buttons are needed for minimized windows or the user will be confused
-time and date are useful
-session menu shows the name of the logged-in user (helpful to the admin)
-action buttons gives a logout menu

+A launcher can be added to the panel for programs of interest to your users (Chrome or Firefox, LibreOffice).  There is a problem with panel launchers applied to all users that will be remedied later.

+This would be a good point to stop and back up the installation if you want to experiment.

+The next steps lock the panel to a system standard.  Understand that by default each user’s home folder determines the desktop settings unless a systemwide file overrides it.  For example for user visitor the path is:
/home/visitor/.config/xfce4/xfconf/xfce-perchannel-xml
and the path for an override file will be inside
/etc/xdg/xdg-xubuntu/xfce-4/xfconf/xfce-perchannel-xml
Also understand that in the XML files that XFCE uses (which can be edited with Leafpad), the lead item in a file, the channel parameter, overrides the lesser property parameters beneath it.  Locking the channel locks everything in the file.  Further, items referred to in the xdg directory should point to system items, not items in a specific user’s home folder.  This last point will be clearer shortly.  If you have removed XFCE Session from the login screen, then you can ignore the xfce4 folding in xdg.

+If you are satisfied with the top panel in the admin’s desktop, copy xfce4-panel.xml from the .config folder noted above (using the correct user’s name!) to the sytem folder noted above.  An easy way to do this is via sudo thunar and opt to show hidden files (.config is normally hidden) and copy and paste.  Now open xcfe4.panel.xml in the system folder (right click, open with Leafpad), and edit the channel line:
<channel name="xfce4-panel" version="1.0" locked="@GROUP-NAME" unlocked="ADMIN-NAME">
and save it.  The phrasing between the quotes is either just a user’s name, or a group (using @ prior).  Locking a user or group and leaving the admin unlocked means the admin can try additional edits and repeat this process later if desired, though the lock edits and others will need to be repeated too.

+If launchers have been placed on the admin panel, they will not work in on the user desktop as they reference a shortcut in the admin’s configuration.  For example, I placed Chromium and LibreOffice launchers on the panel.  The system shortcuts can be seen in /usr/share/applications if you need a reference.  Using Leafpad to edit xfce4-panel.xml in the system folder, I changed one (longnumber).desktop to chromium-browser.desktop (or firefox.desktop) and the other to libreoffice-startcenter.desktop to correct this.

+If you only want your users to access a couple of programs, why offer a fuller menu on the panel?  A limited panel can be created via the steps above, and then subsequently the unlocked admin can pin the full applications menu back on the admin’s panel if desired.  Alternatively, the user or the system menu can be edited using the Menu tool or directly at:  xfce-applications.menu (there is one in the user’s config files that gets merged with the system one).

+The process used for xfce4-panel.xml can be repeated for xfce4-desktop.xml.  However, there is a shortcut if you only have one user beyond the admin.  This one works within the user login.  The objective is to remove the rightclick shortcuts on the desktop.  If you have opted to leave the Applications Menu on the panel of the limited user, the path is:  Settings Manager > Desktop where under Menu you should clear the rightclick option and next clear the list of default icons and opt for none as icon type on the Icon tab.  If you have removed Applications Menu from the panel of the limited user, you can click SUPER R to bring up the applications and find Settings Manager.  Again, this is all done within the login of the limited user.  If you plan to have multiple users, then apply the previous method involving the xdg folder with a xfce4-panel.xml file.

+Once you like what you have, this would be another good point to do a backup if you want to trial different browsers.  I will detail what I found it took to control Firefox, and then how I successfully locked down Chromium (much easier).

+The challenge is locking down the web browser.  Firefox (default for Xubuntu) stores the user preferences under a specific user (visitor in this example) within a subfolder of the hidden folder /home/vistor/.mozilla as a prefs.js file.  Changes to preferences such as the home page as stored to this file.  If the preferred settings to the browser are made and the browser is closed, the prefs.js file can be opened with Leafpad and saved as a user.js file in the same user folder.  Firefox preferentially obeys user.js if it exists instead of the prefs.js file.  The user can still manipulate the browser settings, but the changes simply do not persist once the browser is closed.  This method is user-specific, but the user.js file can be placed in each user’s home folder and it will be applied.  It is the easiest method I have found to control this browser.  But there is a problem in the newer versions of Firefox!  Clicking on Help > Troubleshooting and opting to Reset Firefox blows up all these configurations.

+The Firefox Add-On Public Fox can perform the steps noted above, but, in my testing, it is also destroyed by the reset.  The Add-On Easy Whitelist can be passworded to block access both to preferences (configure them first) as well as blocking access to the rest button.  More on Easy Whitelist subsequently.

+The kiosk tool for Firefox, R-kiosk, is good for offering a browser window without an address bar and without the back/forward arrows (the latter I found to be problematic).  If you wish to test it, I suggest creating a demonstration user as it is not straightforward to deactivate.

+If there is only one user, what is above is probably adequate.  To block access by multiple users to settings systemwide, it is necessary to create a mozilla.cfg file in the folder with the Firefox program (usr/lib/firefox in 12.04).  The syntax is a little different than the prefs.js and user.js file but the concept is the same.  Names of the preferences vary by Firefox version.  Unfortunately there is not a good template available that I could locate.

+This mozilla.cfg file must be referenced in a file placed in the usr/lib/firefox/defaults/pref folder (same location as channel-prefs.js) in Firefox 18.  Create a file using Leafpad called local-settings.js that simply contains:
pref("general.config.obscure_value", 0);
pref("general.config.filename", "mozilla.cfg");
Save the file and these settings will be applied on the next run of Firefox.

+How to enforce limits on sites?  In my testing of Easy Whitelist, I found this product quite adequate for application to one user’s browser.  For more “serious” control of a computer (or for multiple users), especially if the box is to be dedicated to a single purpose (serving as access to a library card catalog in my example), for Firefox, it would be wiser perhaps to use Ubuntu’s firewall software in a whitelist mode.  Either the built-in UFW program can be used in graphical format by downloading GUFW from the Ubuntu Software Center, or the older Firestarter program can be downlownloaded.  Pick one or the other; both should not be running simultaneously.  The firewall can be used in a whitelist mode (i.e. only allowing defined connections).

+All of these steps (including the firewall edits) can be ignored if you opt for the Chromium browser as documented here:
[http://www.chromium.org/administrators/linux-quick-start](http://www.chromium.org/administrators/linux-quick-start)
The installation of one system file controls the browser for all users on that machine, including whitelist/blacklist options!  The Chromium site offers a template file for Linux and includes fairly clear instructions about the choices inside the template.

+The template (you-name-it).json is placed where the browser is installed.  In (X)ubuntu 12.04 the path to /policies/managed/ is slightly different that in the tutorial (but no worries, it is created when the Chromium browser is installed via Ubuntu's Software Center) but it works out of the box.  Make an typographical syntax error, though, and the file won't work.  But using chrome://policies in the address line will show what is working and what is broken, and turning options on and off is as easy as (un)commenting in a text file (i.e. "//").

+As noted, this controls all users on the machine, including the admin.  If this is a problem, one option to give the admin more access is to retain an uncontrolled installation of Firefox and use Chromium as the browser for the users.

+I have tested these steps on a second installation and in a live environment with vibrant teenagers.  I believe that an admin with some experience with the Ubuntu version of Linux can set up a station dedicated to a single, single purpose in an afternoon with some assurance that it won’t be easy to hack.  It will require episodic maintenance (perhaps biweekly).  As always:  backup, backup backup.

I will appreciate your feedback via the Ubuntu forums.

Best wishes.

---

