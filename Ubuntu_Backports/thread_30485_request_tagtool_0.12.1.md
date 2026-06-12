---
title: "request: tagtool 0.12.1"
date: 2005-04-28
forum: Ubuntu Backports
---

### Post by RastaMahata on 2005-04-28
Could it be possible to have TagTool 0.12.1 in Hoary through backports? Oh, and with a Menu entry too? Please? :)

[http://pwp.netcabo.pt/paol/tagtool/](http://pwp.netcabo.pt/paol/tagtool/)

---

### Post by TravisNewman on 2005-04-29
*drool* Incredible. I want it. ;)

---

### Post by MetalMusicAddict on 2005-05-01
Oh... NICE. I use Easytag but this looks nice also. ;)

---

### Post by jdong on 2005-05-01
Sure, I'll get his one through Breezy.

---

### Post by Bob D. on 2005-05-02
I upgraded to 0.12.1 from staging and none of the drop down menus are working. When launched from the command line a bunch of errors are thrown:

 ```

bob@oakraider:~$ tagtool
art_render_invoke: no image source given
art_render_invoke: no image source given

(tagtool:32240): libglade-WARNING **: could not find signal handler 'cb_ctx_unselect_all'.

(tagtool:32240): libglade-WARNING **: could not find signal handler 'cb_show_rename_chconv'.

(tagtool:32240): libglade-WARNING **: could not find signal handler 'cb_check_changed'.

(tagtool:32240): libglade-WARNING **: could not find signal handler 'cb_about_credits'.

(tagtool:32240): libglade-WARNING **: could not find signal handler 'cb_ctx_manual_rename'.

(tagtool:32240): libglade-WARNING **: could not find signal handler 'cb_update_filename'.

(tagtool:32240): libglade-WARNING **: could not find signal handler 'cb_ctx_delete'.

(tagtool:32240): libglade-WARNING **: could not find signal handler 'cb_id3v2_edit'.

(tagtool:32240): libglade-WARNING **: could not find signal handler 'cb_id3_keypress'.

(tagtool:32240): libglade-WARNING **: could not find signal handler 'cb_vor_view_simple'.

(tagtool:32240): libglade-WARNING **: could not find signal handler 'cb_name_set'.

(tagtool:32240): libglade-WARNING **: could not find signal handler 'cb_playlist_go'.

(tagtool:32240): libglade-WARNING **: could not find signal handler 'cb_select_dir'.

(tagtool:32240): libglade-WARNING **: could not find signal handler 'cb_settings_charconv'.

(tagtool:32240): libglade-WARNING **: could not find signal handler 'cb_dlg_progress_size_changed'.

(tagtool:32240): libglade-WARNING **: could not find signal handler 'cb_vor_view_button'.

(tagtool:32240): libglade-WARNING **: could not find signal handler 'cb_vor_add'.

(tagtool:32240): libglade-WARNING **: could not find signal handler 'cb_tag_go'.
(tagtool:32240): libglade-WARNING **: could not find signal handler 'cb_file_quit'.

(tagtool:32240): libglade-WARNING **: could not find signal handler 'cb_vor_remove'.

(tagtool:32240): libglade-WARNING **: could not find signal handler 'cb_clear_go'.

(tagtool:32240): libglade-WARNING **: could not find signal handler 'cb_vor_tag_changed'.

(tagtool:32240): libglade-WARNING **: could not find signal handler 'cb_tag_help'.

(tagtool:32240): libglade-WARNING **: could not find signal handler 'cb_chconv_save'.

(tagtool:32240): libglade-WARNING **: could not find signal handler 'cb_rename_help'.

(tagtool:32240): libglade-WARNING **: could not find signal handler 'cb_files_button_press'.

(tagtool:32240): libglade-WARNING **: could not find signal handler 'cb_files_popup_menu'.

(tagtool:32240): libglade-WARNING **: could not find signal handler 'cb_r_invalid_omit_toggled'.

(tagtool:32240): libglade-WARNING **: could not find signal handler 'cb_id3v2_frame_row_activated'.

(tagtool:32240): libglade-WARNING **: could not find signal handler 'cb_toggle_recurse'.

(tagtool:32240): libglade-WARNING **: could not find signal handler 'cb_r_conv_space_none_toggled'.

(tagtool:32240): libglade-WARNING **: could not find signal handler 'cb_notebook_switch'.

(tagtool:32240): libglade-WARNING **: could not find signal handler 'cb_id3v1_create_tag'.

(tagtool:32240): libglade-WARNING **: could not find signal handler 'cb_id3v2_view_advanced'.

(tagtool:32240): libglade-WARNING **: could not find signal handler 'cb_main_win_size_changed'.

(tagtool:32240): libglade-WARNING **: could not find signal handler 'cb_show_tag_chconv'.

(tagtool:32240): libglade-WARNING **: could not find signal handler 'cb_sort_field'.

(tagtool:32240): libglade-WARNING **: could not find signal handler 'cb_prefs_save'.

(tagtool:32240): libglade-WARNING **: could not find signal handler 'cb_t_conv_space_none_toggled'.

(tagtool:32240): libglade-WARNING **: could not find signal handler 'cb_id3_remove_tag'.

(tagtool:32240): libglade-WARNING **: could not find signal handler 'cb_help_contents'.

(tagtool:32240): libglade-WARNING **: could not find signal handler 'cb_id3v2_view_button'.

(tagtool:32240): libglade-WARNING **: could not find signal handler 'cb_settings_id3prefs'.

(tagtool:32240): libglade-WARNING **: could not find signal handler 'cb_vor_edit'.

(tagtool:32240): libglade-WARNING **: could not find signal handler 'cb_field_changed'.

(tagtool:32240): libglade-WARNING **: could not find signal handler 'cb_id3_copyv1tov2'.

(tagtool:32240): libglade-WARNING **: could not find signal handler 'cb_id3_write_changes'.

(tagtool:32240): libglade-WARNING **: could not find signal handler 'cb_id3_tag_changed'.

(tagtool:32240): libglade-WARNING **: could not find signal handler 'cb_id3_copyv2tov1'.

(tagtool:32240): libglade-WARNING **: could not find signal handler 'cb_id3v2_create_tag'.

(tagtool:32240): libglade-WARNING **: could not find signal handler 'cb_rename_go'.

(tagtool:32240): libglade-WARNING **: could not find signal handler 'cb_about_close'.

(tagtool:32240): libglade-WARNING **: could not find signal handler 'cb_wd_changed'.

(tagtool:32240): libglade-WARNING **: could not find signal handler 'cb_id3v2_add'.

(tagtool:32240): libglade-WARNING **: could not find signal handler 'cb_vor_keypress'.

(tagtool:32240): libglade-WARNING **: could not find signal handler 'cb_id3v2_view_simple'.

(tagtool:32240): libglade-WARNING **: could not find signal handler 'cb_file_refresh'.

(tagtool:32240): libglade-WARNING **: could not find signal handler 'cb_id3v2_remove'.

(tagtool:32240): libglade-WARNING **: could not find signal handler 'cb_dlg_progress_stop'.

(tagtool:32240): libglade-WARNING **: could not find signal handler 'cb_main_win_delete'.

(tagtool:32240): libglade-WARNING **: could not find signal handler 'cb_vor_view_advanced'.

(tagtool:32240): libglade-WARNING **: could not find signal handler 'cb_wd_keypress'.

(tagtool:32240): libglade-WARNING **: could not find signal handler 'cb_dlg_scan_stop'.

(tagtool:32240): libglade-WARNING **: could not find signal handler 'cb_vor_comment_row_activated'.

(tagtool:32240): libglade-WARNING **: could not find signal handler 'cb_vor_write'.

(tagtool:32240): libglade-WARNING **: could not find signal handler 'cb_help_about'.

(tagtool:32240): libglade-WARNING **: could not find signal handler 'cb_vor_clear'.
bob@oakraider:~$


``` 

I searched for a .tagtool directory thinking to delete the prefs file to see if that would work. However, I couldn't locate a .tagtool directory. I downgraded back to 0.11.1, which then worked without throwing errors when launched from the command line and the drop downs work. I still wasn't able to locate a prefs file for this version either.

Bob

---

### Post by ow50 on 2005-05-02
[QUOTE=Bob D.]I upgraded to 0.12.1 and none of the drop down menus are working. [/QUOTE]

I remember I got the same when I tried it. I tried both traditional installing from source and building from the debian unstable source.

---

### Post by jdong on 2005-05-02
Ok, with those two reports, this backport will be **deleted** from the staging tree within a couple of days....

Those who've tried this backport, please remove and reinstall tagtool sometime next week :) (or just downgrade)

---

### Post by Bob D. on 2005-05-27
Looks like the problems we saw with Audio Tag Tool have been fixed in the new version  0.12.2:

[font=Arial][size=2][i]"This release fixes the problems some people were experiencing when Audio Tag Tool is compiled against the latest version of Gnome/GTK (UI didn't respond to events, lots of libglade warnings).
[/i] 
* There are also new translations for Russian, Ukranian, Bulgarian and Lithuanian*."


Can we try the backport again?


Thanks!

Bob[/size][/font]

---

### Post by jdong on 2005-05-27
As soon as it enters Breezy :)

---

### Post by Confuse on 2005-07-10
[QUOTE=jdong]As soon as it enters Breezy :)[/QUOTE]

Has this ever hit breezy? How can I check? If it has, do you think you can backport it?

---

### Post by Bob D. on 2005-07-10
>  Has this ever hit breezy?Nope.

 > How can I check? [http://packages.ubuntu.com/]("http://packages.ubuntu.com/")

I wrote to the Debian maintainer and asked if it could be upgraded to 0.12.2 in unstable. I'd suggest you do the same Confuse. Since Ubuntu is built off Debian, the package has to hit the Debian repos before it will hit the Ubuntu repos.

Here;s a page with info on the Debian maintainer:

[http://packages.qa.debian.org/t/tagtool.html]("http://packages.qa.debian.org/t/tagtool.html")

Bob

---

### Post by Bob D. on 2005-07-10
OK, just heard back from the Debian maintainer for tagtool. He's putting together an updated package right now.

I've got to file a wishlist bug for him to close and we're good to go with 0.12.2 in Debian. After that it should hit Breezy pretty quick, Hopefully the Breezy package freeze hasn't hit yet.

Bob

---

### Post by Bob D. on 2005-07-10
> Debian Bug#317695: Acknowledgement (tagtool: Request to update version in unstable to 0.12.2) 

Wishlist bug was accepted. Looks like we're on our way.

Bob

---

### Post by Confuse on 2005-07-10
[QUOTE=Bob D.]Wishlist bug was accepted. Looks like we're on our way.

Bob[/QUOTE]

Awesome! Can't wait!

---

### Post by Bob D. on 2005-08-08
OK, tagtool 0.12.2 has made it into Debian unstable. Any idea why it hasn't sync'ed to Breezy's Universe? It's been in Debian unstable since Friday 8/5.

Bob

---

### Post by Confuse on 2005-08-12
[QUOTE=Bob D.]OK, tagtool 0.12.2 has made it into Debian unstable. Any idea why it hasn't sync'ed to Breezy's Universe? It's been in Debian unstable since Friday 8/5.

Bob[/QUOTE]

Any status of the backport of this?

---

### Post by Bob D. on 2005-08-12
I filed a bug with the "Ubuntu Masters of the Universe" (MOTU) the other day:

 > Public bug reported:
[https://launchpad.net/malone/bugs/1709]("https://launchpad.net/malone/bugs/1709")

Affects: Ubuntu tagtool
       Severity: Normal
       Priority: Medium
         Status: New

Description:
0.12.2 version is out that fixes problem. From the author:

This release fixes the problems some people were experiencing when Audio Tag
Tool is compiled against the latest version of Gnome/GTK (UI didn't respond to
events, lots of libglade warnings).


Debian has merged this newer version into unstable as of Friday 8/5. Is it
possible to get this into Breezy's Universe?  Tagtool is not usable on Hoary
right now. We need this into Breezy so it can be backported. And of course
Breezy needs this for tagtool to be usable.

Bob 

No reponse yet from the MOTU team. Confuse, perhaps you can add any additional comments to the bug at the bug link at the to of my bug report above.

Bob

---

### Post by Seth on 2005-08-12
[QUOTE=Confuse]Any status of the backport of this?[/QUOTE]
 Breezy has hit freeze, so you need to wait for a backport from Perky.

---

### Post by Bob D. on 2005-08-13
Thanks for that Seth, I was wondering if that was indeed the case.

I saw a posting somewhere that the MOTU's can break the freeze under certain circumstances. While tagtool 0.12.1 won't work right now in Hoary (and I assume Breezy), it may not be important enough of a package to get an over ride done.

I filed the bug to see what might happen.  ;-) 

Bob

---

### Post by Seth on 2005-08-13
[QUOTE=Bob D.]Thanks for that Seth, I was wondering if that was indeed the case.

I saw a posting somewhere that the MOTU's can break the freeze under certain circumstances. While tagtool 0.12.1 won't work right now in Hoary (and I assume Breezy), it may not be important enough of a package to get an over ride done.

I filed the bug to see what might happen.  ;-) 

Bob[/QUOTE]
 Sure, if the package in Breezy won't work, MOTUs will break freeze. What's the bug number?

---

### Post by Bob D. on 2005-08-13
Here you go Seth:

[https://launchpad.net/malone/bugs/1709](https://launchpad.net/malone/bugs/1709)

Bob

---

