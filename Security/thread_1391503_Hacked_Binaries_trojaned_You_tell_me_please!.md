---
title: "Hacked? Binaries trojaned? You tell me please!"
date: 2010-01-26
forum: Security
---

### Post by njiii on 2010-01-26
I've created a blog, rather than post mounds of string data here, for this thread. 

Is something injecting rogue code into my binaries? Please help me evaludate this, please post here about it not on my blog, take a look at the strings in my binaries which I believe to be infected. 

[http://oddlinuxstrings.wordpress.com](http://oddlinuxstrings.wordpress.com) 

It's more permanent than a pastebin, otherwise I'd use a pastebin service. Please tell me if you see anything odd.

---

### Post by Agent ME on 2010-01-26
What makes you think your system is hacked? Because certain strings in your programs look like gibberish? Binaries aren't meant to be readable.

---

### Post by njiii on 2010-01-26
I'm not much of a blogger, the posts aren't all showing up, so here are individual links: 

[http://oddlinuxstrings.wordpress.com/2010/01/27/ssh-binarys-strings/](http://oddlinuxstrings.wordpress.com/2010/01/27/ssh-binarys-strings/) [http://oddlinuxstrings.wordpress.com/2010/01/27/md5sum-binarys-strings/](http://oddlinuxstrings.wordpress.com/2010/01/27/md5sum-binarys-strings/) [http://oddlinuxstrings.wordpress.com/2010/01/27/iptables-binarys-strings/](http://oddlinuxstrings.wordpress.com/2010/01/27/iptables-binarys-strings/) [http://oddlinuxstrings.wordpress.com/2010/01/27/grep-binarys-strings/](http://oddlinuxstrings.wordpress.com/2010/01/27/grep-binarys-strings/) [http://oddlinuxstrings.wordpress.com/2010/01/27/gpg-binarys-strings/](http://oddlinuxstrings.wordpress.com/2010/01/27/gpg-binarys-strings/) [http://oddlinuxstrings.wordpress.com/2010/01/27/cryptsetup-binarys-strings/](http://oddlinuxstrings.wordpress.com/2010/01/27/cryptsetup-binarys-strings/) [http://oddlinuxstrings.wordpress.com/2010/01/27/aptitude-binarys-strings/](http://oddlinuxstrings.wordpress.com/2010/01/27/aptitude-binarys-strings/) 

What do you make of the strings, please?

---

### Post by njiii on 2010-01-26
What makes you think your system is hacked? Because certain strings in your programs look like gibberish? Binaries aren't meant to be readable.  Please, serious replies only discussing the topic and strings.  YES! Binaries ARE meant to be readable with certain tools, like hexdump, strings, objdump, and more.  Please help me. Thank you.

---

### Post by Seq on 2010-01-26
> **njiii said:**
> What makes you think your system is hacked? Because certain strings in your programs look like gibberish? Binaries aren't meant to be readable.  Please, serious replies only discussing the topic and strings.  YES! Binaries ARE meant to be readable with certain tools, like hexdump, strings, objdump, and more.  Please help me. Thank you.

And? Are you getting an error, or just not understanding the output?

If you're curious, you can sha1sum or md5sum a specific curious file, download and unpack the .deb that contains it on another computer, and sha1sum it there and compare.

You can also check the md5sum on the iso itself with those provided on Ubuntu's main release server.

[http://releases.ubuntu.com/9.10/MD5SUMS]("http://releases.ubuntu.com/9.10/MD5SUMS")

---

### Post by njiii on 2010-01-27
Thank you, but I'm beyond the capability of trusting binaries or source on my local network and must at this point inquire for outside assistance. Many people on different forums have requested I post the strings for these binaries I suspect are trojaned for their examination. I've done so. I'm told examining these strings and knowing which individual ones stand out as rogue strings IS something which is simple to those in the know. I hope someone may point out some of the strings which stand out, thank you my friends. It's my hope someone may find some strings which are bad and educate me as to why, briefly. I'm aware of other means of examining integrity of files, it's failed because I cannot trust anything on my network. Comparisons of hashes differ or fail, my router could be hacked for all I know as fresh media installed downloads files which make my system behave strangely and I'm chasing down ghosted shells. 

Please help me with these strings, I've exhausted other avenues of verification. If I can get to the heart of this infection by examining the strings of the binaries, I may be able to isolate the exact problem and defeat it. This is my point of defense, please help me with it, not open virtual chutes into other discussions which lead away from this topic or other means or places to try, this is my question, this is my thread, this is my call for help.

---

### Post by lisati on 2010-01-27
Please define what you mean by "binaries"......when I see the term, I usually think of executable programs (meant to be excuted, not read) or data that is stored in a form that is better suited to data processing than it is for reading on a screen.

---

### Post by djchandler on 2010-01-27
Your request is dubious to say the least. I doubt anyone with common sense will click on your links due to your unorthodox presentation, and the lack of any supporting facts. The risk of launching some executable or script by clicking on your links that are outside of this forum is something I'm certainly not prepared to do, and I recommend that all others should avoid doing so.

Your post is being reported to administrators so that it may be quarantined and evaluated.

---

### Post by adam814 on 2010-01-27
If you really think you've been hacked and "rootkitted" like that why are you still running the system?  I'd save any relevant data and reinstall, then worry about figuring out what happened and why later (unless of course it wasn't a system I needed daily).

Here's another thought: Why not boot a LiveCD (you can't infect read-only media post-burning at least).  You could manually download relevant packages like chkrootkit and rkhunter and extract them to the proper directories on your hard disk to install them.  Then chroot into your system and run them.  That way you're only using executables from trusted media and it will scan the relevant binaries for you.

---

### Post by cariboo on 2010-01-27
First, where are you getting your .deb packages from? If they aren't from the repositories, then whatever problems you are having are because you are downloading packages from an untrusted source.

If the files in the repositories were hacked, don't you think there would be much more about it here in the forums?

All the packages in the repositories are built and packaged in a build farm, there is no human intervention between the time the sources is submitted and the packages are placed in the repositories.

Instead of looking for strange strings in binary packages, you can download the source from the repositories and check the code line by line yourself, to see if there is anything strange.

---

### Post by Seq on 2010-01-27
> **njiii said:**
> Thank you, but I'm beyond the capability of trusting binaries or source on my local network and must at this point inquire for outside assistance. Many people on different forums have requested I post the strings for these binaries I suspect are trojaned for their examination. I've done so. I'm told examining these strings and knowing which individual ones stand out as rogue strings IS something which is simple to those in the know.

Odd. SHA1 or MD5 sums would give you a fingerprint of files you can compare with on-line. The iso image has an MD5sum you can compare with. Updates, which you would download online, are again in a big list of MD5Sums. This list is cryptographically signed so that your machine can verify that it is an official list. Assuming you haven't gone and installed random unverified stuff on your system, you can trust this.

If you installed unverified stuff or added any other public keys to your apt keyring, then you're pretty much SOL. If you can't trust what's on the system, you can't trust the system. There are guards there to help defend against man-in-the-middle attacks and some weird hostle network providers, but if you bypass that you get what you get.

That said, you're going to have to find a pretty bored community member to troll through strings output looking for some unknown indication that it was modified (why would they insert strings?). If you were worried about a specific application being compromised, just re-fetch and re-install that application, and verify the checksums. If you're worried about every application, then you're going to find somebody to crawl through 2301 files. And that's just /usr/bin (on my system), there are countless libraries that could be modified.

Good luck!

---

### Post by njiii on 2010-01-27
How many hoops do I have to jump through here for a serious reply directly answering yes or no and why I do or do not have infected binaries? For all I know someone in control of my router could be replying to try and dissuade an answer here. So now I have to defend against offtopic attacks: 

**"Your request is dubious to say the least."** 

Do you understand my request? No, my request is valid. Thank you for not attempting to help me. 

There is no quarentine required, I posted on a quick blog I created so I didn't flood this forum with lengthy strings. If you cannot help me, please do not post to this thread, it's very simple! If you don't know what a binary is, please search Google and yes I've searched Google for these strings but I need someone with knowledge to tell me yes or tell me no and why or why not.

Here is an example, they are strings, this isn't anything executable, here is a copy of synaptic's strings where I'm questioning whether anything bad is listed inside, NOTHING HERE IS EXECUTABLE!!! 

```
 /lib/ld-linux.so.2 D@ ! yLIl fyIk dT&#8217;`J] b.y8mU 7rQ2 A.cV qJ1i libapt-pkg-libc6.10-6.so.4.8 __gmon_start__ _Jv_RegisterClasses pthread_cancel _ZN10pkgAcquire4Item8FinishedEv _ZNSt15basic_stringbufIcSt11char_traitsIcESaIcEED1Ev _ZNK13Configuration8FindFileEPKcS1_ _Z9TFRewriteP8_IO_FILERK13pkgTagSectionPPKcP13TFRewriteData _Z12pkgFixBrokenR11pkgDepCache _ZN10OpProgress4DoneEv _ZSt16__insertion_sortIN9__gnu_cxx17__normal_iteratorIPSsSt6vectorISsSaISsEEEEEvT_S7_ _ZN11pkgDepCache8MarkKeepERKN8pkgCache11PkgIteratorEbbm _ZN11pkgDepCache12MarkRequiredERNS_13InRootSetFuncE _ZN13pkgSourceList12ReadMainListEv _Z11flExtensionSs _Z9flCombineSsSs _ZN10pkgAcquire4Item5StartESsm _ZSt25__unguarded_linear_insertIN9__gnu_cxx17__normal_iteratorIPSsSt6vectorISsSaISsEEEESsEvT_T0_ _ZN11GlobalError10PopMessageERSs _ZN11CommandLine5ParseEiPPKc _ZN10pkgTagFileC1EP6FileFdm _ZN10OpProgress6UpdateEv _ZN8pkgCache11DepIterator6GlobOrERS0_S1_ _ZNSt8_Rb_treeISsSt4pairIKSsSsESt10_Select1stIS2_ESt4lessISsESaIS2_EE10_M_insert_EPKSt18_Rb_tree_node_baseSB_RKS2_ _ZN13Configuration5ClearESs _ZN12MD5SummationC1Ev _ZN17pkgArchiveCleaner2GoESsR8pkgCache _Z12StringToBoolRKSsi _ZN13ConfigurationC1EPKNS_4ItemE _ZN18pkgProblemResolverC1EP11pkgDepCache _Z9TimeToStrm _ZTV13pkgTagSection _ZN10pkgAcquire3RunEi _Z14ParseQuoteWordRPKcRSs _Z13_strtabexpandPcj _ZN10pkgAcquire4Item9IsTrustedEv _Z13URItoFileNameRKSs _ZN10pkgTagFile4StepER13pkgTagSection _ZN17pkgPackageManager17DoInstallPostForkEi _ZN8pkgCache15PkgFileIterator6RelStrEv _ZStplIcSt11char_traitsIcESaIcEESbIT_T0_T1_ERKS6_S8_ _ZSt16__introsort_loopIN9__gnu_cxx17__normal_iteratorIPSsSt6vectorISsSaISsEEEEiEvT_S7_T0_ _ZN10pkgAcquire7EnqueueERNS_8ItemDescE _Z13pkgInitConfigR13Configuration _ZN11CommandLineD1Ev _ZN13Configuration3SetEPKci _ZN16pkgAcquireStatus5PulseEP10pkgAcquire _ZN8pkgCacheC1EP4MMapb _ZN11GlobalError7WarningEPKcz _ZTV16pkgAcquireStatus _ZNSt6vectorISsSaISsEED1Ev _ZSt9make_heapIN9__gnu_cxx17__normal_iteratorIPSsSt6vectorISsSaISsEEEEEvT_S7_ _ZN10pkgTagFileD1Ev _ZTV10OpProgress _ZTIN10pkgAcquire4ItemE _Z9SizeToStrd _ZN10pkgAcquire4Item16Custom600HeadersEv _ZNSt8_Rb_treeISsSsSt9_IdentityISsESt4lessISsESaISsEE10_M_insert_EPKSt18_Rb_tree_node_baseS8_RKSs _ZN11GlobalError7DiscardEv _ZN11pkgDepCache5SweepEv _ZN10pkgAcquire4Item7HashSumEv _ZN10pkgAcquire8ItemDescD1Ev _Z14pkgApplyStatusR11pkgDepCache _ZN10pkgAcquire11FetchNeededEv _ZN10pkgRecords6LookupERKN8pkgCache16DescFileIteratorE _ZN16pkgAcquireStatus4StopEv _Z14ReadConfigFileR13ConfigurationRKSsbj _ZTV6FileFd _ZNK13Configuration4FindEPKcS1_ _ZN11pkgDepCache4InitEP10OpProgress _ZN17pkgPackageManager10FixMissingEv _ZNK13pkgTagSection5FindSEPKc _ZN10OpProgress11CheckChangeEf _ZN10pkgAcquire4ItemC2EPS_ _ZN10pkgAcquire4Item6FailedESsPNS_12MethodConfigE _fini _Z8CopyFileR6FileFdS0_ _ZN16pkgAcquireStatus5StartEv _ZNK8pkgCache11VerIterator21TranslatedDescriptionEv _Z9flNotFileSs _ZN11pkgDepCache19SetCandidateVersionEN8pkgCache11VerIteratorE _ZStplIcSt11char_traitsIcESaIcEESbIT_T0_T1_ERKS6_PKS3_ _ZN10pkgRecordsD1Ev _ZSt22__final_insertion_sortIN9__gnu_cxx17__normal_iteratorIPSsSt6vectorISsSaISsEEEEEvT_S7_ _Z18pkgMakeStatusCacheR13pkgSourceListR10OpProgressPP4MMapb _ZN6FileFd4OpenESsNS_8OpenModeEm _ZN4MMapC1ER6FileFdm _Z8flNotDirSs _ZN13ConfigurationD1Ev _ZNSt8_Rb_treeISsSt4pairIKSsSsESt10_Select1stIS2_ESt4lessISsESaIS2_EE8_M_eraseEPSt13_Rb_tree_nodeIS2_E _Z13pkgInitSystemR13ConfigurationRP9pkgSystem _ZTS10OpProgress _ZNSs12_S_constructIPcEES0_T_S1_RKSaIcESt20forward_iterator_tag _ZNK11MD5SumValue5ValueEv _ZStplIcSt11char_traitsIcESaIcEESbIT_T0_T1_EPKS3_RKS6_ _ZN10OpProgress8ProgressEm _Z7GetLockSsb _ZNK13pkgTagSection4FindEPKcRS1_S2_ _ZN18pkgProblemResolver14InstallProtectEv _ZN6FileFd4SizeEv _ZN13pkgSourceListD1Ev _ZN10OpProgress15OverallProgressEmmmRKSs _ZN10OpProgressD0Ev _ZN8pkgCache7FindPkgERKSs _ZN10pkgAcquireD1Ev _ZN13Configuration3SetEPKcRKSs _ZNSt8_Rb_treeISsSsSt9_IdentityISsESt4lessISsESaISsEE8_M_eraseEPSt13_Rb_tree_nodeISsE _ZN10pkgAcquire4Item9ShortDescEv _config _Z11ReadPinFileR9pkgPolicySs _ZN11GlobalError5ErrorEPKcz _ZNSt4pairIKSsSsED1Ev _ZN10pkgAcquire5CleanESs _ZN13Configuration5ClearESsi _ZN10pkgAcquire4ItemD2Ev _ZN10OpProgressD1Ev _ZNSt8_Rb_treeIiiSt9_IdentityIiESt4lessIiESaIiEE8_M_eraseEPSt13_Rb_tree_nodeIiE _Z14pkgDistUpgradeR11pkgDepCache _Z13pkgAllUpgradeR11pkgDepCache _ZN13ConfigurationC1Ev _Z8ioprintfRSoPKcz _ZN6FileFdD1Ev _ZN10pkgAcquire8ShutdownEv _ZN12MD5Summation6ResultEv _ZNK13Configuration5FindIEPKci _ZN10pkgAcquire10WorkerStepEPNS_6WorkerE _ZN10pkgAcquire4Item4DoneESsmSsPNS_12MethodConfigE _ZN11pkgDepCache11ActionGroupD1Ev _ZN11pkgDepCacheC1EP8pkgCachePNS_6PolicyE _ZNSt6vectorISsSaISsEEC1ERKS1_ _ZN10OpProgressD2Ev _ZN13pkgSourceListC1Ev _ZN11pkgDepCache12SetReInstallERKN8pkgCache11PkgIteratorEb _ZN16pkgAcquireStatus7FetchedEmm _Z9_strstripPc _ZN8pkgCdrom3AddEP14pkgCdromStatus _ZNSt8_Rb_treeISsSt4pairIKSsSsESt10_Select1stIS2_ESt4lessISsESaIS2_EE17_M_insert_unique_ESt23_Rb_tree_const_iteratorIS2_ERKS2_ _ZN8pkgCache8CompTypeEh _Z9StrToTimeRKSsRl _Z10FileExistsSs _ZN11pkgDepCache10MarkDeleteERKN8pkgCache11PkgIteratorEbmb _ZNK8pkgCache11VerIterator12DownloadableEv _ZNSt6vectorIP17re_pattern_bufferSaIS1_EE13_M_insert_auxEN9__gnu_cxx17__normal_iteratorIPS1_S3_EERKS1_ _ZN13pkgTagSection4ScanEPKcm _ZN13Configuration6LookupEPKcb _ZN10OpProgressC1Ev _ZN8pkgCache8PriorityEh _ZN9pkgPolicyC1EP8pkgCache TFRewritePackageOrder _ZN15pkgVersionMatchD1Ev _ZN11pkgDepCache11ActionGroupC1ERS_ _ZN11pkgDepCache8MarkAutoERKN8pkgCache11PkgIteratorEb _ZN11CommandLineC1EPNS_4ArgsEP13Configuration _ZN10pkgAcquireC1EP16pkgAcquireStatus _ZN10pkgRecordsC1ER8pkgCache _ZN10OpProgress11SubProgressEm _ZTI16pkgAcquireStatus _ZN10OpProgressC2Ev _ZN15pkgVersionMatchC1ESsNS_9MatchTypeE _ZN10pkgRecords6LookupERKN8pkgCache15VerFileIteratorE _ZN6FileFd4SeekEm _ZSt13__adjust_heapIN9__gnu_cxx17__normal_iteratorIPSsSt6vectorISsSaISsEEEEiSsEvT_T0_S8_T1_ _Z13stringcasecmpPKcS0_S0_S0_ _ZNK13Configuration7FindDirEPKcS1_ _Z18pkgMinimizeUpgradeR11pkgDepCache _ZNSt8_Rb_treeISsSt4pairIKSsSsESt10_Select1stIS2_ESt4lessISsESaIS2_EE16_M_insert_uniqueERKS2_ _Z8SubstVarRKSsS0_S0_ _ZN17pkgPackageManager11GetArchivesEP10pkgAcquireP13pkgSourceListP10pkgRecords _Z11QuoteStringRKSsPKc _ZN8pkgCache7DepTypeEh _ZN12MD5Summation5AddFDEim _ZN11GlobalError10DumpErrorsEv _ZN18pkgProblemResolver7ResolveEb _ZN11pkgDepCache14writeStateFileEP10OpProgressb _Z12_GetErrorObjv _ZNK13Configuration5FindBEPKcb _ZN18pkgProblemResolverD1Ev _Z10ListUpdateR16pkgAcquireStatusR13pkgSourceListi _ZN15pkgVersionMatch4FindEN8pkgCache11PkgIteratorE _ZN16pkgAcquireStatusC2Ev _ZN11GlobalError5ErrnoEPKcS1_z _ZNSt6vectorISsSaISsEE13_M_insert_auxEN9__gnu_cxx17__normal_iteratorIPSsS1_EERKSs _ZN11pkgDepCache11MarkInstallERKN8pkgCache11PkgIteratorEbmbb _ZN8pkgCache11PkgIteratorppEi _ZTI10OpProgress _ZNSt8_Rb_treeISsSsSt9_IdentityISsESt4lessISsESaISsEE16_M_insert_uniqueERKSs _ZNK13pkgSourceList9FindIndexEN8pkgCache15PkgFileIteratorERP12pkgIndexFile _Z9LookupTagRKSsPKcS2_ libapt-inst-libc6.10-6.so.1.1 _ZN10debDebFileC1ER6FileFd _ZTV12pkgDirStream _ZN10debDebFile17MemControlExtract4ReadERS_ _ZN10debDebFile17MemControlExtractD1Ev _ZTVN10debDebFile17MemControlExtractE _ZN9ARArchiveD1Ev libglade-2.0.so.0 gtk_container_get_children gdk_color_parse g_value_unset gtk_text_view_get_type gtk_progress_bar_get_type gtk_widget_get_name gtk_menu_item_set_submenu gtk_cell_renderer_text_new gtk_tooltips_new gtk_label_new gtk_table_get_type gtk_check_menu_item_get_type g_strdup gtk_tool_item_get_type gtk_widget_get_type gtk_color_selection_get_type g_list_free gtk_image_new_from_stock gtk_file_chooser_get_type gtk_label_set_text gtk_dialog_get_type gtk_image_menu_item_get_type g_malloc gtk_menu_get_type gtk_image_menu_item_set_image gtk_combo_box_get_type g_value_set_boxed g_object_new gtk_container_get_type gtk_option_menu_get_type gtk_option_menu_set_history g_value_set_string g_string_free gdk_pixbuf_get_type gtk_adjustment_get_type gtk_expander_get_type gdk_color_get_type gtk_editable_get_type gtk_window_get_type g_object_set_data gtk_image_new_from_file g_return_if_fail_warning g_object_set gtk_paned_get_type gtk_clist_get_type gtk_tree_model_get_type gtk_list_store_append gtk_label_get_type gtk_object_get_type gtk_option_menu_set_menu g_type_check_instance_is_a gtk_button_get_type g_list_last gtk_widget_grab_focus gtk_tooltips_set_tip gtk_entry_get_type gtk_combo_get_type g_signal_connect_data g_type_check_instance_cast gtk_widget_show gtk_list_store_new g_strsplit gtk_container_add gtk_color_selection_dialog_get_type gtk_toggle_button_set_active gtk_toggle_button_get_type gtk_list_store_set gtk_tool_item_set_tooltip g_value_init gtk_clist_column_titles_show g_list_prepend g_value_set_object gtk_misc_get_type gtk_tool_button_get_type gdk_colormap_alloc_color gtk_tree_view_get_type gtk_menu_item_get_type gtk_image_new_from_pixbuf g_string_truncate gtk_notebook_get_type gtk_scrolled_window_get_type g_error_free gtk_message_dialog_get_type gtk_text_buffer_set_text gtk_clist_set_column_width g_object_set_property gtk_toolbar_get_type gtk_font_selection_dialog_get_type gtk_spin_button_get_type gtk_image_get_type g_type_class_peek_parent g_log g_file_test gtk_misc_set_alignment glade_xml_new glade_xml_signal_connect_data glade_xml_get_type glade_xml_get_widget libgtk-x11-2.0.so.0 g_utf8_validate g_dir_close gdk_color_copy g_dir_read_name g_value_get_string g_date_new_dmy g_io_channel_unix_new g_object_get_data g_value_set_pointer g_strrstr g_markup_escape_text g_object_get_property g_list_foreach gdk_cursor_new gdk_x11_drawable_get_xid g_string_new gdk_window_set_transient_for gdk_window_object_get_type g_timeout_add_seconds g_strdup_printf g_locale_from_utf8 pango_font_description_from_string gdk_draw_rectangle g_type_register_static gdk_event_get_time gdk_window_get_state pango_layout_get_pixel_size g_strchomp gdk_pixbuf_get_from_drawable g_str_has_prefix g_strchug g_source_remove gdk_draw_layout XSync pango_layout_set_text gdk_pixmap_new pango_layout_set_font_description pango_layout_new gdk_window_set_cursor g_locale_to_utf8 g_list_first g_strfreev g_type_add_interface_static g_string_append_printf g_dir_open g_pattern_match_simple gtk_message_dialog_set_markup gtk_tree_view_column_set_visible gtk_progress_bar_set_pulse_step gtk_main_iteration gtk_list_store_remove gtk_init gtk_box_pack_start gtk_text_view_new gtk_tree_model_row_inserted gtk_clist_set_text gtk_clist_thaw gtk_tree_view_get_vadjustment gtk_label_set_markup gtk_scrolled_window_new gtk_widget_reparent gtk_image_set_from_file gtk_window_get_modal gtk_tree_view_get_hadjustment gtk_clist_freeze gtk_tree_selection_path_is_selected gtk_font_selection_dialog_get_font_name gtk_message_dialog_new_with_markup gtk_window_move gtk_widget_set_sensitive gtk_paned_get_position gtk_image_set_from_stock gtk_clist_set_column_auto_resize gtk_clist_new_with_titles gtk_text_buffer_get_type gtk_dialog_response gtk_cell_renderer_pixbuf_new gtk_window_new gtk_clist_row_is_visible gtk_button_new_with_label gtk_adjustment_value_changed gtk_box_get_type gtk_table_attach gtk_list_store_move_after gtk_tree_path_get_indices gtk_main gtk_tree_store_append gtk_tree_iter_free gtk_widget_get_style gtk_window_resize gtk_entry_set_text gtk_window_set_modal gtk_toolbar_set_style gtk_combo_set_popdown_strings gtk_tree_model_filter_new gtk_window_maximize gtk_settings_get_default gtk_list_store_clear gtk_tree_view_set_search_column gtk_color_selection_get_current_color gtk_expander_get_expanded gtk_font_selection_dialog_set_font_name gtk_tree_model_iter_has_child gtk_tree_iter_copy gtk_text_buffer_apply_tag_by_name gtk_tree_view_get_selection gtk_tree_model_filter_get_type gtk_editable_select_region gtk_notebook_set_show_tabs gtk_separator_menu_item_new gtk_entry_append_text gtk_tree_view_get_column gtk_tree_model_iter_n_children gtk_entry_new gtk_icon_theme_get_default gtk_cell_renderer_text_set_fixed_height_from_font gtk_tree_selection_select_iter gtk_tree_path_compare gtk_window_set_resizable gtk_combo_box_append_text gtk_dialog_new gtk_tree_model_get gtk_text_view_set_cursor_visible gtk_progress_bar_new gtk_clist_remove gtk_tree_view_set_cursor gtk_button_clicked gtk_text_buffer_get_iter_at_offset gtk_spin_button_set_value gtk_dialog_get_content_area gtk_icon_theme_load_icon gtk_table_new gtk_tool_button_set_icon_name gtk_frame_new gtk_text_buffer_insert_with_tags_by_name gtk_check_menu_item_get_active gtk_tree_view_column_set_sizing gtk_tree_view_remove_column gtk_clist_moveto gtk_window_set_title gtk_check_button_new_with_label gtk_tree_path_free gtk_clist_select_row gtk_button_set_label gtk_tree_model_get_iter_first gtk_vbox_new gtk_event_box_new gtk_tree_sortable_sort_column_changed gtk_clist_append gtk_option_menu_remove_menu gtk_list_store_swap gtk_text_tag_table_lookup gtk_window_set_skip_taskbar_hint gtk_table_set_col_spacings gtk_tree_view_scroll_to_cell gtk_widget_queue_resize gtk_tree_path_get_depth gtk_tree_path_prev gtk_list_store_get_type gtk_signal_compat_matched gtk_list_store_move_before gtk_tree_view_get_columns gtk_tooltips_get_type gtk_adjustment_set_value gtk_notebook_remove_page gtk_widget_set_uposition gtk_text_view_get_buffer gtk_tree_path_prepend_index gtk_color_selection_set_current_color gtk_tree_store_set gtk_file_chooser_get_filename gtk_toggle_button_get_active gtk_vscrollbar_new gtk_tree_path_new_from_string gtk_option_menu_get_menu gtk_check_menu_item_set_active gtk_menu_shell_append gtk_combo_box_get_model gtk_tree_selection_get_selected_rows gtk_window_set_default_size gtk_binding_set_find gtk_text_buffer_get_tag_table gtk_message_dialog_new gtk_tree_path_append_index gtk_widget_show_all gtk_widget_hide gtk_text_buffer_get_end_iter gtk_combo_box_set_active gtk_label_set_label gtk_signal_connect_full gtk_tree_view_set_model gtk_window_set_position gtk_file_chooser_set_extra_widget gtk_plug_new gtk_window_set_transient_for gtk_progress_bar_pulse gtk_tree_sortable_set_sort_column_id gtk_tree_view_column_set_fixed_width gtk_tree_model_row_deleted gtk_image_menu_item_new_with_label gtk_tree_model_get_path gtk_spin_button_get_value_as_int gtk_tree_model_get_string_from_iter gtk_tree_view_expand_all gtk_combo_box_remove_text gtk_text_view_set_wrap_mode gtk_text_view_add_child_at_anchor gtk_window_present gtk_scrolled_window_set_policy gtk_progress_bar_update gtk_text_buffer_get_char_count gtk_entry_get_text gtk_text_buffer_delete gtk_dialog_set_default_response gtk_tree_model_iter_next gtk_paned_set_position gtk_clist_get_row_data gtk_cell_renderer_toggle_new gtk_binding_entry_add_signal gtk_dialog_run gtk_menu_shell_get_type gtk_option_menu_get_history gtk_menu_item_new_with_label gtk_menu_get_active gtk_combo_box_get_active_text gtk_label_get gtk_object_get_data gtk_list_store_insert gtk_menu_item_activate gtk_tree_view_set_rules_hint gtk_tree_model_filter_set_visible_func gtk_color_selection_dialog_new gtk_text_buffer_insert gtk_tree_view_get_bin_window gtk_clist_clear gtk_scrolled_window_set_shadow_type gtk_file_chooser_dialog_new gtk_object_set_data gtk_spin_button_get_value gtk_tree_path_new gtk_widget_realize gtk_text_buffer_create_tag gtk_label_get_text gtk_dialog_add_button gtk_clist_set_row_data gtk_widget_set_size_request gtk_text_iter_forward_line gtk_notebook_set_current_page gtk_text_iter_get_line gtk_widget_modify_font gtk_cell_renderer_text_get_type gtk_tree_sortable_get_type gtk_expander_set_expanded gtk_font_selection_dialog_new gtk_tree_selection_set_mode gtk_menu_new gtk_tree_view_column_new_with_attributes gtk_widget_set_usize gtk_text_buffer_get_iter_at_line_index gtk_tree_path_next gtk_tree_view_get_path_at_pos gtk_tree_store_new gtk_text_buffer_insert_at_cursor gtk_tree_selection_get_selected gtk_tree_path_new_first gtk_window_get_urgency_hint gtk_widget_modify_bg gtk_progress_bar_set_text gtk_tree_selection_unselect_all gtk_message_dialog_format_secondary_text gtk_text_buffer_apply_tag gtk_main_quit gtk_window_set_icon gtk_hbox_new gtk_progress_bar_set_fraction gtk_box_pack_end gtk_tree_model_sort_new_with_model gtk_combo_set_value_in_list gtk_widget_queue_draw gtk_text_view_set_left_margin gtk_tree_model_row_changed gtk_container_set_border_width gtk_tree_view_column_get_type gtk_box_pack_start_defaults gtk_window_set_policy gtk_tree_model_get_iter gtk_tree_view_column_set_sort_column_id gtk_text_view_scroll_to_iter gtk_widget_destroy gtk_events_pending gtk_tree_view_column_set_resizable gtk_image_set_from_pixbuf gtk_tree_model_iter_nth_child gtk_text_buffer_get_start_iter gtk_text_buffer_create_child_anchor gtk_menu_popup gtk_tree_view_set_expander_column gtk_tree_selection_select_path gtk_tree_view_get_model gtk_tree_view_append_column gtk_window_set_urgency_hint gtk_window_get_position libxml2.so.2 libgdk-x11-2.0.so.0 gdk_pixbuf_new_from_xpm_data g_spawn_async g_usleep gdk_display gdk_color_alloc gdk_colormap_get_system gdk_window_foreign_new gdk_pango_context_get gdk_drawable_unref libatk-1.0.so.0 libpangoft2-1.0.so.0 libgdk_pixbuf-2.0.so.0 gdk_pixbuf_unref libpangocairo-1.0.so.0 libgio-2.0.so.0 g_child_watch_add g_spawn_close_pid g_io_add_watch g_io_channel_read_chars g_timeout_add libcairo.so.2 libfreetype.so.6 libfontconfig.so.1 libpango-1.0.so.0 libgobject-2.0.so.0 libgmodule-2.0.so.0 libglib-2.0.so.0 g_strstr_len g_date_get_weekday libvte.so.9 vte_terminal_new vte_terminal_set_size vte_terminal_feed_child vte_terminal_set_scrollback_lines vte_reaper_get vte_terminal_forkpty vte_terminal_get_type vte_terminal_feed vte_terminal_set_font_from_string libm.so.6 liblaunchpad-integration.so.1 launchpad_integration_add_items libpthread.so.0 sigaction __errno_location fork connect waitpid read accept write recvmsg sendmsg fcntl libept.so.0 _ZNK6Xapian12TermIteratordeEv _ZN6Xapian4MSetD1Ev _ZNK6Xapian12MSetIterator12get_documentEv _ZNK6Xapian4MSet3endEv _ZN6Xapian5Query8InternalD1Ev _ZN6Xapian12TermIteratorD1Ev _ZN6Xapian12TermIteratorppEv _ZN6Xapian4StemD1Ev _ZN6Xapian5Query18abort_constructionEv _ZN6Xapian7EnquireC1ERKNS_8DatabaseEPNS_12ErrorHandlerE _ZN6Xapian8DatabaseD1Ev _ZNK6Xapian8Database14allterms_beginERKSs _ZN6Xapian5Query18start_constructionENS0_2opEj _ZN6Xapian5QueryD1Ev _ZN6Xapian8DocumentD1Ev _ZN6Xapian5Query16end_constructionEv _ZN6Xapian5Query12add_subqueryERKSs _ZN6Xapian7Enquire9set_queryERKNS_5QueryEj _ZNK6Xapian4MSet5beginEv _ZNK6Xapian7Enquire8get_msetEjjjPKNS_4RSetEPKNS_12MatchDeciderE _ZN6Xapian12TermIteratorC1EPNS0_8InternalE _ZNK6Xapian8Document8get_dataEv _ZN6Xapian7EnquireD1Ev _ZNK3ept10textsearch10TextSearch6expandERN6Xapian7EnquireE _ZNSt3mapISsSsSt4lessISsESaISt4pairIKSsSsEEED1Ev _ZN3ept10textsearch10TextSearchC1Ev _ZNSt4pairISsSsED1Ev _ZNSt8_Rb_treeISsSsSt9_IdentityISsESt4lessISsESaISsEE17_M_insert_unique_ESt23_Rb_tree_const_iteratorISsERKSs _ZSt22__uninitialized_move_aIPSsS0_SaISsEET0_T_S3_S2_RT1_ _ZNSt3setISsSt4lessISsESaISsEED1Ev _ZNSt6vectorIiSaIiEE7reserveEj _ZNSt8_Rb_treeISsSsSt9_IdentityISsESt4lessISsESaISsEE7_M_copyEPKSt13_Rb_tree_nodeISsEPS7_ libxapian.so.15 _ZN6Xapian11QueryParserC1Ev _ZN6Xapian12TermIteratorC1Ev _ZTSN6Xapian5ErrorE _ZN6Xapian11QueryParser10add_prefixERKSsS2_ _ZN6Xapian11QueryParser11parse_queryERKSsjS2_ _ZNK6Xapian4MSet4sizeEv _ZN6Xapian12TermIteratoraSERKS0_ _ZTSN6Xapian12RuntimeErrorE _ZTSN6Xapian13DatabaseErrorE _ZTIN6Xapian12RuntimeErrorE _ZTIN6Xapian20DatabaseOpeningErrorE _ZNSt4listISsSaISsEED1Ev _ZTIN6Xapian13DatabaseErrorE _ZTSN6Xapian20DatabaseOpeningErrorE _ZN6Xapian11QueryParserD1Ev _ZTIN6Xapian5ErrorE _ZN6Xapian5QueryC1ENS0_2opERKS0_S3_ _ZNK6Xapian12MSetIterator11get_percentEv libz.so.1 libstdc++.so.6 _ZSt20__throw_out_of_rangePKc _ZSt7nothrow _ZNKSt15basic_stringbufIcSt11char_traitsIcESaIcEE3strEv __cxa_guard_abort _Znwj _ZNKSs4findEcj _ZSt16__throw_bad_castv _ZTTSt19basic_ostringstreamIcSt11char_traitsIcESaIcEE _ZNSs4_Rep9_S_createEjjRKSaIcE _ZNSs6resizeEjc _ZNSsC1ERKSs _ZNSo3putEc _ZNKSs5rfindEcj _ZTVSt15basic_stringbufIcSt11char_traitsIcESaIcEE _ZSt18_Rb_tree_decrementPSt18_Rb_tree_node_base _ZNSt13basic_filebufIcSt11char_traitsIcEEC1Ev _ZSt19__throw_logic_errorPKc _ZNSi5seekgESt4fposI11__mbstate_tE _ZTTSt18basic_stringstreamIcSt11char_traitsIcESaIcEE _ZNSt13basic_filebufIcSt11char_traitsIcEE4openEPKcSt13_Ios_Openmode _ZNSs12_M_leak_hardEv _ZNSt15_List_node_base4hookEPS_ _ZSt18_Rb_tree_decrementPKSt18_Rb_tree_node_base _ZNSs6assignERKSs _ZSt20__throw_length_errorPKc _ZSt4endlIcSt11char_traitsIcEERSt13basic_ostreamIT_T0_ES6_ _ZNSt8ios_baseD2Ev _ZTVSt14basic_ifstreamIcSt11char_traitsIcEE __cxa_rethrow _ZTVN10__cxxabiv120__si_class_type_infoE _ZSt4cout _ZNSs9_M_mutateEjjj _ZSt2wsIcSt11char_traitsIcEERSt13basic_istreamIT_T0_ES6_ _ZNSs7reserveEj _ZTVSt14basic_ofstreamIcSt11char_traitsIcEE _ZNSo9_M_insertIbEERSoT_ _Znaj _ZTVSt18basic_stringstreamIcSt11char_traitsIcESaIcEE _ZSt18_Rb_tree_incrementPKSt18_Rb_tree_node_base _ZNSolsEi __cxa_pure_virtual _ZNSt9basic_iosIcSt11char_traitsIcEE5clearESt12_Ios_Iostate _ZNSt13basic_filebufIcSt11char_traitsIcEE5closeEv _ZTTSt14basic_ifstreamIcSt11char_traitsIcEE _ZNSt15_List_node_base6unhookEv _ZTVSt15basic_streambufIcSt11char_traitsIcEE _ZSt29_Rb_tree_insert_and_rebalancebPSt18_Rb_tree_node_baseS0_RS_ _ZSt16__ostream_insertIcSt11char_traitsIcEERSt13basic_ostreamIT_T0_ES6_PKS3_i _ZNSs6assignEPKc _ZNSsC1EPKcjRKSaIcE _ZSt4cerr _ZTTSt19basic_istringstreamIcSt11char_traitsIcESaIcEE _ZNKSs7compareEPKc _ZdlPvRKSt9nothrow_t _ZNSt13basic_filebufIcSt11char_traitsIcEED1Ev __cxa_begin_catch _ZStlsISt11char_traitsIcEERSt13basic_ostreamIcT_ES5_PKc _ZNSi7getlineEPcic _ZTVSt19basic_ostringstreamIcSt11char_traitsIcESaIcEE _ZTVSt19basic_istringstreamIcSt11char_traitsIcESaIcEE _ZNSsC1EPKcRKSaIcE __cxa_guard_acquire _ZNSo9_M_insertImEERSoT_ _ZSt17__throw_bad_allocv _ZNSt8ios_base4InitC1Ev _ZSt3cin _ZSt7getlineIcSt11char_traitsIcESaIcEERSt13basic_istreamIT_T0_ES7_RSbIS4_S5_T1_ES4_ _ZNSt6localeC1Ev _ZNSt9basic_iosIcSt11char_traitsIcEED2Ev _ZTTSt14basic_ofstreamIcSt11char_traitsIcEE _ZNSt18basic_stringstreamIcSt11char_traitsIcESaIcEED1Ev _ZNSs4_Rep20_S_empty_rep_storageE _ZNSi10_M_extractIbEERSiRT_ _ZNSt19basic_istringstreamIcSt11char_traitsIcESaIcEED1Ev _ZnwjRKSt9nothrow_t _ZNSt15basic_streambufIcSt11char_traitsIcEED2Ev _ZNSs7_M_leakEv _ZStrsIcSt11char_traitsIcESaIcEERSt13basic_istreamIT_T0_ES7_RSbIS4_S5_T1_E _ZNSs6appendEjc _ZNSs4swapERSs _ZNSsD1Ev _ZTVSt13basic_filebufIcSt11char_traitsIcEE _ZNSo9_M_insertIlEERSoT_ _ZStlsIcSt11char_traitsIcESaIcEERSt13basic_ostreamIT_T0_ES7_RKSbIS4_S5_T1_E _ZNSt15basic_stringbufIcSt11char_traitsIcESaIcEE7_M_syncEPcjj _ZNSt19basic_ostringstreamIcSt11char_traitsIcESaIcEED1Ev _ZNSsC1ERKSsjj _ZdlPv _ZNSt9basic_iosIcSt11char_traitsIcEE4initEPSt15basic_streambufIcS1_E _ZNSo5flushEv _ZTVSt9basic_iosIcSt11char_traitsIcEE __cxa_end_catch _ZSt4clog _ZNKSt5ctypeIcE13_M_widen_initEv _ZNSt8ios_baseC2Ev __dynamic_cast _ZNSs6appendEPKcj _ZTVN10__cxxabiv121__vmi_class_type_infoE _ZNSt8ios_base4InitD1Ev _ZNSt6localeD1Ev _ZNSt14basic_ifstreamIcSt11char_traitsIcEED1Ev _ZNKSs7compareERKSs _ZNSt15_List_node_base8transferEPS_S0_ _ZNSt14basic_ofstreamIcSt11char_traitsIcEED1Ev _ZSt9terminatev __cxa_guard_release _ZNKSs4findEPKcjj _ZNSs4_Rep10_M_destroyERKSaIcE __gxx_personality_v0 _ZSt18_Rb_tree_incrementPSt18_Rb_tree_node_base _ZTVN10__cxxabiv117__class_type_infoE __cxa_get_exception_ptr _ZNSs6assignEPKcj _ZNSt15_List_node_base4swapERS_S0_ _ZdaPv _ZNSs6appendERKSs _ZNSt12__basic_fileIcED1Ev libgcc_s.so.1 _Unwind_Resume libc.so.6 _IO_stdin_used strcasestr socket fflush strcpy gmtime_r fnmatch readdir fopen strrchr isalpha regexec pipe perror ngettext getpwuid closedir isblank strncpy sigprocmask regfree __stack_chk_fail unlink listen mkdir _exit popen kill bind_textdomain_codeset strftime chmod __assert_fail strtod isspace strtol fgets strlen __cxa_atexit sigemptyset memset strstr bind memcmp unsetenv __fprintf_chk sigaddset ctime putenv fputs memcpy fclose nl_langinfo opendir getenv sscanf regcomp __snprintf_chk getuid strncasecmp pclose rename localtime strchr rindex __xstat memmove bindtextdomain __strcat_chk strcmp strerror __libc_start_main strcoll libX11.so.6 _edata __bss_start GCC_3.0 CXXABI_1.3.1 GLIBCXX_3.4.11 GLIBCXX_3.4.9 CXXABI_1.3 GLIBCXX_3.4 GLIBC_2.0 GLIBC_2.4 GLIBC_2.1.3 GLIBC_2.3.4 GLIBC_2.2 GLIBC_2.2.3 GLIBC_2.1 PTRh 0[^] 0[^] [^_] Y[^_] [^_] B,+B( [^_] 9{Dt# 9sHu [^_] A,+A( [^_] [^_] [^_] ,[^_] Q,+Q( ,[^_] B,+B( ,[^_] [^_] [^_] Q,+Q( [^_] L[^_] L[^_]
```

---

### Post by Seq on 2010-01-27
> **njiii said:**
> How many hoops do I have to jump through here for a serious reply directly answering yes or no and why I do or do not have infected binaries? For all I know someone in control of my router could be replying to try and dissuade an answer here. So now I have to defend against offtopic attacks: 

**"Your request is dubious to say the least."** 

Do you understand my request? No, my request is valid. Thank you for not attempting to help me.

Actually, we *do* understand the issue. We've tried to tell you how you can verify for yourself. There *are* security measures to verify what gets installed. Instead, you have decided to ignore the help of the community members who may, believe it or not, know what they are talking about before they start replying.

Besides, if somebody is in control of your router and replying here (with helpful information, I may add) to try and dissuade you, then why ask at all?

"No, you are not hacked".

That, logically, should not make you feel any safer.

---

### Post by lisati on 2010-01-27
That looks nothing like a bunch of binaries. It looks more like an unformatted list of stuff that you *might* have on your system. Good luck getting a helpful reply. :)

Hint: to keep the formatting of a text file you might be quoting, use tags around them e.g. [noparse]```
 (text) 
```[/noparse] This will make it a lot easier for us to read and interpret.

---

### Post by djchandler on 2010-01-27
I have no idea what you think you are seeing, but if you want to help with Ubuntu code, you can get a Launchpad account and do your bug hunting with the people who write and maintain the code.

I apologize. Possibly you will find someone who speaks your language at Launchpad.

Go to:
[https://launchpad.net/](https://launchpad.net/)

---

### Post by Seq on 2010-01-27
> **lisati said:**
> That looks nothing like a bunch of binaries. It looks more like an unformatted list of stuff that you *might* have on your system. Good luck getting a helpful reply. :)

He's basically running `strings` on executable files and expecting us to tell him if his executable is hacked without seeing the actual executable parts.

EDIT: I should add that I wouldn't even go through the executable part. If he just did 'md5sum /some/file`, some kind folk would say "Yeah, that's what I have too, running with -updates and -proposed, so YMMV". But instead....

---

### Post by lisati on 2010-01-27
> **Seq said:**
> He's basically running `strings` on executable files and expecting us to tell him if his executable is hacked without seeing the actual executable parts.

That helps explain why I'm absolutely baffled by the output he provided. "strings" might provide one or two clues (if we're really lucky) but I have a strong suspicion that there are better tools for troubleshooting a system that *might* have been damaged by malware.

---

### Post by baddog144 on 2010-01-27
I have no idea how OP expects anyone to really be able to tell him anything useful based on that output. For one, it's huge and not really worth anyone's time to go through. However, a cursory glance suggests nothing is particularly out of order. It's really very hard to tell though

---

### Post by schauerlich on 2010-01-27
```
[^_]
[^_]
[^_]
L[^_]
<[^_]
<[^_
[^_]
;z |
[^_]
[^_]
```

Once the hacker pwns ur r00tz, he'll draw this little dancing guy on your screen just to taunt you. This guy's good.


[size=1]but seriously, nothing to worry about.[/size]

---

### Post by cariboo on 2010-01-27
After this:

> How many hoops do I have to jump through here for a serious reply directly answering yes or no and why I do or do not have infected binaries? For all I know someone in control of my router could be replying to try and dissuade an answer here. So now I have to defend against offtopic attacks: 

The best answer you're going to get here is:

> nobody can tell from the gibberish you posted, whether your file is infected or not.

I would suggest you decompile the binary in question, you can get a decompiler [here]("http://www.google.ca/search?sourceid=chrome&ie=UTF-8&q=decompile+a+linux+binary+file"), and check out the source.

With that, nothing is going to get solved here, this thread is closed.

---

