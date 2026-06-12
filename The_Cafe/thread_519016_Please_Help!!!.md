---
title: "Please Help!!!"
date: 2007-08-06
forum: The Cafe
---

### Post by PrimoTurbo on 2007-08-06
Can someone please go into their

/usr/share/icons/Tango/scalable/actions

and upload the following files for me: (if they have any of them)
[B]dialog-close.svg 
gtk-quit.png
gtk-ok.svg
gtk-yes.svg
dialog-apply.svg
stock-apply.svg[/B]

I messed up something and deleted some of them...

---

### Post by ~LoKe on 2007-08-06
I don't have **any** of those. o_O

---

### Post by PrimoTurbo on 2007-08-06
are you sure?

[http://www.taimila.com/?q=node/3](http://www.taimila.com/?q=node/3)

Here is a list of some misc icon improvements that I have made to my dapper. Human icon theme doesn't include all icons, which leads to ugly icons in some applications. Here are some improvements that I have found good.

Change OK-button icon to Tango style and Quit icon from file menu. Do the following in terminal.
cd /usr/share/icons/Tango/scalable/actions
sudo ln -s dialog-close.svg gtk-quit.png
sudo ln -s dialog-apply.svg gtk-ok.svg
sudo ln -s dialog-apply.svg gtk-yes.svg
sudo ln -s dialog-apply.svg stock-apply.svg
cd /usr/share/icons/
sudo gtk-update-icon-cache --force Tango

I did this once it worked, I changed icon themes and re-did for a different theme and worked and after that I can't find the icons..

---

### Post by ~LoKe on 2007-08-06
Yep.

> loke@x04d:~$ ls /usr/share/icons/Tango/scalable/actions
address-book-new.svg           gtk-strikethrough.svg
add.svg                        gtk-underline.svg
appointment-new.svg            gtk-undo-ltr.svg
appointment.svg                gtk-unindent-ltr.svg
back.svg                       gtk-unindent.svg
bookmark_add.svg               kfind.svg
bookmark-new.svg               kfm_home.svg
bookmarks_list_add.svg         leftjust.svg
bottom.svg                     list-add.svg
centrejust.svg                 list-remove.svg
contact-new.svg                lock.svg
document-new.svg               mail_forward.svg
document-open.svg              mail-forward.svg
document-print-preview.svg     mail-mark-junk.svg
document-print.svg             mail-message-new.svg
document-properties.svg        mail_new.svg
document-save-as.svg           mail_replyall.svg
document-save.svg              mail-reply-all.svg
down.svg                       mail-reply-sender.svg
edit-clear.svg                 mail_reply.svg
editclear.svg                  mail-send-receive.svg
edit-copy.svg                  mail_spam.svg
editcopy.svg                   media-eject.svg
edit-cut.svg                   media-playback-pause.svg
editcut.svg                    media-playback-start.svg
edit-delete.svg                media-playback-stop.svg
editdelete.svg                 media-record.svg
edit-find-replace.svg          media-seek-backward.svg
edit-find.svg                  media-seek-forward.svg
edit-paste.svg                 media-skip-backward.svg
editpaste.svg                  media-skip-forward.svg
edit-redo.svg                  next.svg
edit-select-all.svg            player_eject.svg
edit-undo.svg                  player_end.svg
exit.svg                       player_fwd.svg
filefind.svg                   player_pause.svg
filenew.svg                    player_play.svg
fileopen.svg                   player_record.svg
fileprint.svg                  player_rew.svg
filequickprint.svg             player_start.svg
filesaveas.svg                 player_stop.svg
filesave.svg                   previous.svg
find.svg                       process-stop.svg
finish.svg                     redhat-home.svg
folder_new.svg                 redo.svg
folder-new.svg                 reload3.svg
format-indent-less.svg         reload_all_tabs.svg
format-indent-more.svg         reload_page.svg
format-justify-center.svg      reload.svg
format-justify-fill.svg        remove.svg
format-justify-left.svg        rightjust.svg
format-justify-right.svg       search.svg
format-text-bold.svg           start.svg
format-text-italic.svg         stock_add-bookmark.svg
format-text-strikethrough.svg  stock_bottom.svg
format-text-underline.svg      stock_copy.svg
forward.svg                    stock_cut.svg
gnome-lockscreen.svg           stock_delete.svg
gnome-logout.svg               stock_down.svg
gnome-searchtool.svg           stock_file-properites.svg
gnome-session-logout.svg       stock_first.svg
gnome-stock-mail-fwd.svg       stock_fullscreen.svg
gnome-stock-mail-new.svg       stock_help-add-bookmark.svg
gnome-stock-mail-rpl.svg       stock_home.svg
gnome-stock-text-indent.svg    stock_last.svg
gnome-stock-text-unindent.svg  stock_left.svg
go-bottom.svg                  stock_mail-compose.svg
go-down.svg                    stock_mail-forward.svg
go-first.svg                   stock_mail-reply.svg
go-home.svg                    stock_mail-reply-to-all.svg
gohome.svg                     stock_mail-send-receive.svg
go-jump.svg                    stock_media-fwd.svg
go-last.svg                    stock_media-next.svg
go-next.svg                    stock_media-pause.svg
go-previous.svg                stock_media-play.svg
go-top.svg                     stock_media-prev.svg
go-up.svg                      stock_media-rec.svg
gtk-add.svg                    stock_media-rew.svg
gtk-bold.svg                   stock_media-stop.svg
gtk-clear.svg                  stock_new-address-book.svg
gtk-copy.svg                   stock_new-appointment.svg
gtk-cut.svg                    stock_new-bcard.svg
gtk-delete.svg                 stock_new-dir.svg
gtk-find-and-replace.svg       stock_new-tab.svg
gtk-find.svg                   stock_new-text.svg
gtk-fullscreen.svg             stock_new-window.svg
gtk-go-back-ltr.svg            stock_paste.svg
gtk-go-back-rtl.svg            stock_print-preview.svg
gtk-go-down.svg                stock_print.svg
gtk-go-forward-ltr.svg         stock_properties.svg
gtk-go-forward-rtl.svg         stock_redo.svg
gtk-goto-bottom.svg            stock_refresh.svg
gtk-goto-first-ltr.svg         stock_right.svg
gtk-goto-first-rtl.svg         stock_save-as.svg
gtk-goto-last-ltr.svg          stock_save.svg
gtk-goto-last-rtl.svg          stock_search-and-replace.svg
gtk-goto-top.svg               stock_search.svg
gtk-go-up.svg                  stock_select-all.svg
gtk-home.svg                   stock_spam.svg
gtk-indent-ltr.svg             stock_stop.svg
gtk-indent.svg                 stock_text_bold.svg
gtk-italic.svg                 stock_text_center.svg
gtk-jump-to-ltr.svg            stock_text_indent.svg
gtk-jump-to-rtl.svg            stock_text_italic.svg
gtk-justify-center.svg         stock_text_justify.svg
gtk-justify-fill.svg           stock_text_left.svg
gtk-justify-left.svg           stock_text_right.svg
gtk-justify-right.svg          stock_text-strikethrough.svg
gtk-media-forward-ltr.svg      stock_text_underlined.svg
gtk-media-forward-rtl.svg      stock_text_unindent.svg
gtk-media-next-ltr.svg         stock_top.svg
gtk-media-next-rtl.svg         stock_undo.svg
gtk-media-pause.svg            stock_up.svg
gtk-media-play-ltr.svg         stop.svg
gtk-media-previous-ltr.svg     system-lock-screen.svg
gtk-media-previous-rtl.svg     system-log-out.svg
gtk-media-record.svg           system-search.svg
gtk-media-rewind-ltr.svg       system-shutdown.svg
gtk-media-rewind-rtl.svg       tab_new.svg
gtk-media-stop.svg             tab-new.svg
gtk-new.svg                    text_bold.svg
gtk-open.svg                   text_italic.svg
gtk-paste.svg                  text_strike.svg
gtk-print-preview.svg          text_under.svg
gtk-print.svg                  top.svg
gtk-properties.svg             undo.svg
gtk-redo-ltr.svg               up.svg
gtk-refresh.svg                view-fullscreen.svg
gtk-remove.svg                 view-refresh.svg
gtk-save-as.svg                window_fullscreen.svg
gtk-save.svg                   window_new.svg
gtk-select-all.svg             window-new.svg
gtk-stop.svg                   xfce-system-lock.svg

---

### Post by init1 on 2007-08-06
> **PrimoTurbo said:**
> Can someone please go into their

/usr/share/icons/Tango/scalable/actions

and upload the following files for me: (if they have any of them)
[B]dialog-close.svg 
gtk-quit.png
gtk-ok.svg
gtk-yes.svg
dialog-apply.svg
stock-apply.svg[/B]

I messed up something and deleted some of them...
Yeah, I don't have any of them. Why do you need them? Does you gtk theme not work?

---

### Post by PrimoTurbo on 2007-08-06
Basically I need to fix these icons.

[img]http://i103.photobucket.com/albums/m128/envyouraudience/oldicons.png[/img]

I fixed them before but no idea what happened.

---

### Post by edd07 on 2007-08-06
You could try the Tango Homepage: [http://tango.freedesktop.org/Tango_Icon_Gallery]("http://tango.freedesktop.org/Tango_Icon_Gallery")
and find the icons you need.

Hope this helps

---

### Post by PrimoTurbo on 2007-08-06
The icons don't exist there.

---

### Post by DoctorMO on 2007-08-06
> The icons don't exist there.

I find it hard to believe that they don't exist on the creators website, did you check cvs/svn repositories as well as releases? Unless tango didn't make them.

---

### Post by PrimoTurbo on 2007-08-06
I think Tango didn't make them, anyways does anyone know how to change them manually for Tango?..

---

### Post by PrimoTurbo on 2007-08-06
Okay I fixed it, this is what I did. I copied directory from Tangerine icon theme. Located in /usr/share/icons/Tangerine/20x20/actions

The whole 20x20 directory was copied and placed into a new directory I made in ~/.icons/Tango

I then took the /usr/share/icons/Tango/index.theme make a copy of it and put in /home/primo/.icons/Tango/

I then edied the index.theme and added **20x20/actions** under # Directory list
and also added a 
[20x20/actions]
Size=20
Context=Actions
Type=Fixed

Entry now I have nice icons and they fit perfect with Tango, got to love how you can fix these things in linux.

[img]http://img395.imageshack.us/img395/8363/screenshotactionsfilebrfe8.png[/img]

---

### Post by wersdaluv on 2007-08-06
I think the easier way, although I am unsure if it works, is to completely remove then reinstall the icon theme.

---

### Post by PrimoTurbo on 2007-08-06
> **wersdaluv said:**
> I think the easier way, although I am unsure if it works, is to completely remove then reinstall the icon theme.

I did that, but I soon realized that the icons never existed for Tango anyways.

---

