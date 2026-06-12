---
title: "Newest Version of Xiphos that will build in Ubuntu CE 12.04"
date: 2015-04-28
forum: Ubuntu Christian Edition
---

### Post by ronbu on 2015-04-28
I'm testing to see what is the newest version of Xiphos which will successfully build in Ubuntu Christian Edition 12.04 Precise.  The latest version of Xiphos at the time of this post is 4.0.2.  That version I have installed on my two Ubuntu GNOME installs, versions 14.04 and 15.04, thanks to Crosswire's Unit 193 PPA.  But, that PPA does not have a Precise repository.  I have tried to build Xiphos 4.0.2.  I have successfully built dependencies Sword 1.7.4 and the latest Biblesync.  But, I failed to build Xiphos 4.0.2.  I got past the ./waf configure stage.  But when I tried ./waf build , I got the following result.  

```
Build failed:  -> task failed (err #1): 
    {task: cxx_link locale_set_2.o,marshal_2.o,about_modules_2.o,about_sword_2.o,about_trans_2.o,about_xiphos_2.o,bibletext_2.o,bibletext_dialog_2.o,bookmark_dialog_2.o,bookmarks_menu_2.o,bookmarks_treeview_2.o,cipher_key_dialog_2.o,commentary_2.o,commentary_dialog_2.o,dialog_2.o,dictlex_2.o,dictlex_dialog_2.o,display_info_2.o,dummy_2.o,export_bookmarks_2.o,export_dialog_2.o,find_dialog_2.o,font_dialog_2.o,gbs_2.o,gbs_dialog_2.o,gui_2.o,ipc_2.o,main_menu_2.o,main_window_2.o,menu_popup_2.o,mod_mgr_2.o,navbar_book_2.o,navbar_book_dialog_2.o,navbar_versekey_2.o,navbar_versekey_dialog_2.o,navbar_versekey_editor_2.o,navbar_versekey_parallel_2.o,parallel_dialog_2.o,parallel_tab_2.o,parallel_view_2.o,preferences_dialog_2.o,search_dialog_2.o,search_sidebar_2.o,sidebar_2.o,sidebar_dialog_2.o,splash_2.o,tabbed_browser_2.o,treekey-editor_2.o,utilities_2.o,xiphos_2.o,gs_stringmgr_1.o,module_manager_1.o,sword_main_1.o,slib-editor_1.o,link_dialog_1.o,biblesync_glue_1.o,configs_1.o,display_1.o,export_passage_1.o,global_ops_1.o,lists_1.o,main_1.o,mod_mgr_1.o,module_dialogs_1.o,modulecache_1.o,navbar_1.o,navbar_book_1.o,navbar_book_dialog_1.o,navbar_versekey_1.o,parallel_view_1.o,prayerlists_1.o,previewer_1.o,search_dialog_1.o,search_sidebar_1.o,settings_1.o,sidebar_1.o,sword_1.o,sword_treekey_1.o,tab_history_1.o,url_1.o,xml_1.o,marshal_1.o,xiphos_html_1.o,marshal_1.o,wk-html_1.o -> xiphos}

```

The failure to build Xiphos on 4.0.2 means you'll probably have to run Ubuntu 14.04 or later to run Xiphos 4.x on Ubuntu.  Next, I'll try to build the last version of Xiphos 3.x, Xiphos 3.2.2.

---

### Post by ronbu on 2015-04-28
The build of Xiphos 3.2.2 also failed with the same error messages as before.

---

### Post by ronbu on 2015-04-28
The latest version of Xiphos I was able to successfully build in Ubuntu CE 12.04 was Xiphos 3.1.6 was is the next bugfix release after Xiphos 3.1.5 which ships with Ubuntu CE 12.04.  It requires Sword 1.7.x.  I had to rebuild Sword.  I'll have to rebuild Biblememorizer to fit that version of Sword.  The user will have to rebuild Bibletime if the user wants Bibletime.

---

### Post by ronbu on 2015-04-29
I finally was successful at building and installing Xiphos 3.2.2 on Ubuntu CE 12.04.  This time I built an earlier version of biblesync (1.0.2) and then built Xiphos 3.2.2.

---

### Post by ronbu on 2015-04-29
This time I was successful in building and installing Xiphos 4.0.2 (the latest version at this time) on Ubuntu CE 12.04.  The difference this time was that I enabled the Cmake backport for Ubuntu 12.04 PPA at **ppa:kalakris/cmake** .  Then I installed the cmake version of that PPA which is 2.8.11.2.  Later, I built Biblesync 1.1.2 before I built Xiphos 4.0.2.

---

### Post by ronbu on 2015-08-12
I successfully built the new updated Xiphos 4.0.3 on Ubuntu Christian Edition 12.04.  The following is a screenshot of Xiphos.

[IMG]http://ronbuckman.witnesstoday.org/images/xiphos_current.png[/IMG][IMG]https://scontent-sea1-1.xx.fbcdn.net/hphotos-xtp1/v/t1.0-9/11866382_394854447392343_6021466507623438171_n.png?oh=0f97f829e9d4ac2098d3317b76095cac&oe=5648EC32[/IMG]

---

### Post by ronbu on 2016-02-19
Although, I did build Xiphos 4.0.4 on UCE 12.04 Precise, and rebuilt Sword 1.7.4 and BIblesync 1.1.2; I couldn't load and display many of the modules, including many of the English language modules, on either XIphos or Bibletime 2.10.1.  It is working fine with the same version of Sword on Xubuntu Trusty.  So, I decided to delete the install of UCE.  I am currently using JULinux 10 based on Xubuntu Trusty.  JULinux ships with Xiphos and I can use Crosswire's Unit 193 PPA ([https://launchpad.net/~unit193/+archive/ubuntu/crosswire](https://launchpad.net/~unit193/+archive/ubuntu/crosswire)) to get the latest version of Xiphos on Trusty.  This PPA doesn't support Precise.  Ubuntu Christian Edition is a good work, but it's Precise base isn't working like it used to.

---

### Post by ronbu on 2016-03-22
I reinstalled Ubuntu Christian Edition 12.04 Precise on a separate partition.  Mostly works well.  I was able to get a combination of Sword 1.7.3, Biblesync 1.0.2, Xiphos 3.2.2, and the latest Bibletime to work well.  Google Chrome has dropped support for Precise this month.  Best for Precise users to delete Chrome.  Those who want to run the Blink engine on Precise can run either Opera, Slimjet, or Vivaldi.    I still use the Trusty based JULinux as my main OS.

---

### Post by ronbu on 2016-03-24
I was able to get Xiphos 4.0.4 to work on Ubuntu Christian Edition Precise.  Sword 1.7.4 does not run right with the Precise libraries with the Trusty Hardware Enablement Stack when I tried to on my box.  Therefore, I am using Sword 1.7.3.  The following is a screenshot of Xiphos 4.0.4 running on UCE.

[IMG]http://ronbuckman.witnesstoday.org/images/xiphos-4.0.4.jpg[/IMG]

---

### Post by ronbu on 2016-04-06
I am able to get sword 1.7.4 to work well with Ubuntu CE 12.04 Precise, if libclucene-dev is installed before sword 1.7.4 is compiled.

---

