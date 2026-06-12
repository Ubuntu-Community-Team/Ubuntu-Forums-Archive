---
title: "error al compilar pino en maverick"
date: 2011-01-09
forum: Software
---

### Post by 3nG3ndR0 on 2011-01-09
hola amigos no e podido compilar pino me da un error al hacer el make que detallo a continuación, el ppa no el paquete para maverick.

pasos que sigo:

mkdir build   [COLOR="Red"]ok[/COLOR]
cd build      [COLOR="red"]ok[/COLOR]
cmake ../ -DCMAKE_INSTALL_PREFIX=/usr -DUBUNTU_ICONS=OFF -DENABLE_DEBUG=OFF  [COLOR="red"]ok[/COLOR]

```
ariel@ariel-A770M-A:~/Escritorio/pino-twitter/build$ make
Scanning dependencies of target locales
[  0%] Generating po/lv.mo
[  0%] Generating po/ja.mo
[  0%] Generating po/pl.mo
[  0%] Generating po/ml.mo
[  0%] Generating po/it.mo
[  0%] Generating po/ar.mo
[  0%] Generating po/de.mo
[  0%] Generating po/cs.mo
[  0%] Generating po/fa.mo
[  0%] Generating po/fr.mo
[  0%] Generating po/bn_IN.mo
[  0%] Generating po/sr.mo
[  0%] Generating po/te.mo
[  0%] Generating po/sv.mo
[  0%] Generating po/ru.mo
[  0%] Generating po/es.mo
[  0%] Generating po/nl.mo
[  0%] Generating po/ro.mo
[  0%] Generating po/gl.mo
[  0%] Generating po/uk.mo
[  0%] Generating po/en_GB.mo
[  0%] Generating po/tr.mo
[  0%] Generating po/pt_BR.mo
[  0%] Generating po/zh_CN.mo
[  0%] Generating po/ko_KR.mo
[  0%] Generating po/hu.mo
[  0%] Generating po/pt.mo
[  0%] Generating po/th.mo
[  0%] Generating po/mk.mo
[  0%] Generating po/pa.mo
[ 42%] Built target locales
[ 43%] Generating src/rest_api_timeline.c, src/tray_icon.c, src/rest_api_re.c, src/edit_account.c, src/time_utils.c, src/log_window.c, src/rest_api_acc.c, src/rest_api_user_info.c, src/url_short.c, src/hig_table.c, src/favorites_view_list.c, src/template.c, src/color_utils.c, src/timer.c, src/account_widget.c, src/timeline_list_abstract.c, src/rest_api_direct.c, src/status_view_list.c, src/popups.c, src/user_info_list.c, src/rest_urls.c, src/more_window.c, src/main.c, src/timeline_list.c, src/cache.c, src/accounts.c, src/timeline_direct_list.c, src/status_view_dialog.c, src/main_window.c, src/favorites_view_dialog.c, src/dm_entry.c, src/rest_api_abstract.c, src/status_bar_smart.c, src/re_tweet.c, src/account_action.c, src/userpic.c, src/gtk_style.c, src/prefs.c, src/pref_dialog.c
/home/ariel/Escritorio/pino-twitter/src/accounts.vala:100.4-100.27: warning: unhandled error `GLib.Error'
			dir.make_directory(null);
			^^^^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/accounts.vala:117.37-117.55: warning: unhandled error `GLib.Error'
			var stream = new DataInputStream(acc_file.read(null));
			                                 ^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/accounts.vala:118.14-118.46: warning: unhandled error `GLib.Error'
			content = stream.read_until("", null, null);
			          ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/accounts.vala:174.33-174.36: warning: Argument 2: Cannot pass null to non-null parameter type
		Xml.Ns* ns = new Xml.Ns(null, null, null);
		                              ^^^^
/home/ariel/Escritorio/pino-twitter/src/accounts.vala:174.39-174.42: warning: Argument 3: Cannot pass null to non-null parameter type
		Xml.Ns* ns = new Xml.Ns(null, null, null);
		                                    ^^^^
/home/ariel/Escritorio/pino-twitter/src/accounts.vala:256.3-256.14: warning: `null' incompatible with return type `Auth.Account`
		return null;
		^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/cache.vala:115.4-115.33: warning: unhandled error `GLib.Error'
			cache_dir.make_directory(null);
			^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/cache.vala:40.12-40.56: warning: unhandled error `GLib.RegexError'
		url_re = new Regex("(http://)([a-zA-Z0-9-\\.]+)/(.*)");
		         ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/cache.vala:72.25-72.57: warning: unhandled error `GLib.RegexError'
		string old_url_path = url_re.replace(url, -1, 0, "\\3");
		                      ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/cache.vala:100.4-100.70: warning: unhandled error `GLib.Error'
			yield pick.copy_async(pick_file, FileCopyFlags.NONE, 1, null, null);
			^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/cache.vala:88.4-88.55: warning: unhandled error `GLib.Error'
			pick.copy(pick_file, FileCopyFlags.NONE, null, null);
			^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/cache.vala:120.12-120.78: warning: unhandled error `GLib.Error'
		var en = cache_dir.enumerate_children(FILE_ATTRIBUTE_STANDARD_NAME, 0, null);
		         ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/cache.vala:123.22-123.39: warning: unhandled error `GLib.Error'
		while((file_info = en.next_file(null)) != null) {
		                   ^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/cache.vala:125.4-125.22: warning: unhandled error `GLib.Error'
			d_file.delete(null);
			^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/account_action.vala:41.3-41.6: error: Cannot assign to construct-only properties, use Object (property: value) constructor chain up
		name = "AccountAct";
		^^^^
/home/ariel/Escritorio/pino-twitter/src/account_action.vala:46.18-46.57: warning: unhandled error `GLib.Error'
		default_icon = Icon.new_for_string(Config.USERPIC_PATH);
		               ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/account_action.vala:146.15-146.39: warning: unhandled error `GLib.Error'
		Icon icon = Icon.new_for_string(path);
		            ^^^^^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/gtk_style.vala:44.13-44.40: warning: deprecated syntax, don't use `new' to initialize structs
		Value v = new Value(typeof(Gdk.Color));// = null;
		          ^^^^^^^^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/more_window.vala:31.3-31.6: error: Cannot assign to construct-only properties, use Object (property: value) constructor chain up
		type = WindowType.POPUP;
		^^^^
/home/ariel/Escritorio/pino-twitter/src/prefs.vala:298.4-298.27: warning: unhandled error `GLib.Error'
			dir.make_directory(null);
			^^^^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/prefs.vala:315.37-315.56: warning: unhandled error `GLib.Error'
			var stream = new DataInputStream(pref_file.read(null));
			                                 ^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/prefs.vala:316.14-316.46: warning: unhandled error `GLib.Error'
			content = stream.read_until("", null, null);
			          ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/prefs.vala:440.33-440.36: warning: Argument 2: Cannot pass null to non-null parameter type
		Xml.Ns* ns = new Xml.Ns(null, null, null);
		                              ^^^^
/home/ariel/Escritorio/pino-twitter/src/prefs.vala:440.39-440.42: warning: Argument 3: Cannot pass null to non-null parameter type
		Xml.Ns* ns = new Xml.Ns(null, null, null);
		                                    ^^^^
/home/ariel/Escritorio/pino-twitter/src/re_tweet.vala:33.2-33.20: warning: ReTweet.state hides inherited field `Gtk.Widget.state'. Use the `new' keyword if hiding was intentional
	private State state;
	^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/re_tweet.vala:59.2-59.22: warning: ReTweet.parent hides inherited field `Gtk.Widget.parent'. Use the `new' keyword if hiding was intentional
	private Window parent;
	^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/url_short.vala:47.10-47.62: warning: unhandled error `GLib.RegexError'
		urls = new Regex("((http|https|ftp)://([\\S]+)\\.([\\S]+))");
		       ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/url_short.vala:93.17-93.100: warning: unhandled error `GLib.RegexError'
			bool bingo = urls.match_all_full(text, -1, pos, GLib.RegexMatchFlags.NEWLINE_ANY, out match_info);
			             ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/url_short.vala:143.19-143.65: warning: unhandled error `GLib.RegexError'
		var ur1_regex = new Regex("Your ur1 is: <a href=\"([^\"]+)\">");
		                ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/re_tweet.vala:466.21-466.28: warning: string.len is deprecated. Use string.length
		int length = (int)text.len();
		                  ^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/re_tweet.vala:442.17-442.101: warning: unhandled error `GLib.RegexError'
			bool bingo = regex.match_all_full(text, -1, pos, GLib.RegexMatchFlags.NEWLINE_ANY, out match_info);
			             ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/re_tweet.vala:492.44-492.51: warning: string.len is deprecated. Use string.length
		label.set_text("<b>%s</b>".printf((140 - text.len()).to_string()));
		                                         ^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/re_tweet.vala:171.11-171.46: warning: unhandled error `GLib.RegexError'
		nicks = new Regex("(^|\\s)@([A-Za-z0-9_]+)");
		        ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/re_tweet.vala:172.10-172.62: warning: unhandled error `GLib.RegexError'
		urls = new Regex("((http|https|ftp)://([\\S]+)\\.([\\S]+))");
		       ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/re_tweet.vala:173.10-173.67: warning: unhandled error `GLib.RegexError'
		tags = new Regex("((^|\\s)\\#[A-Za-z0-9_\\p{Latin}\\p{Greek}]+)");
		       ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/prefs.vala:194.24-194.57: warning: unhandled error `GLib.RegexError'
			Regex bold_italic = new Regex("(.*)(Bold Italic)(.*)");
			                    ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/prefs.vala:195.21-195.110: warning: unhandled error `GLib.RegexError'
			Regex re_style = new Regex("([a-zA-Z0-9 _]+) (BoldItalic|Bold|Italic|Medium|Oblique|BoldOblique) ([0-9]+)");
			                 ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/prefs.vala:196.22-196.59: warning: unhandled error `GLib.RegexError'
			Regex re_normal = new Regex("([a-zA-Z0-9 _]+) ([0-9]+)");
			                  ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/prefs.vala:198.20-198.72: warning: unhandled error `GLib.RegexError'
			string my_val = bold_italic.replace(value, -1, 0, "\\1BoldItalic\\3");
			                ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/prefs.vala:201.19-201.56: warning: unhandled error `GLib.RegexError'
				_deFontName = re_style.replace(my_val, -1, 0, "\\1");
				              ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/prefs.vala:202.19-202.56: warning: unhandled error `GLib.RegexError'
				_deFontSize = re_style.replace(my_val, -1, 0, "\\3").to_int();
				              ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/prefs.vala:205.19-205.57: warning: unhandled error `GLib.RegexError'
				_deFontName = re_normal.replace(my_val, -1, 0, "\\1");
				              ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/prefs.vala:206.19-206.57: warning: unhandled error `GLib.RegexError'
				_deFontSize = re_normal.replace(my_val, -1, 0, "\\2").to_int();
				              ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/template.vala:451.40-451.54: warning: unhandled error `GLib.Error'
		var in_stream = new DataInputStream (file.read(null));
		                                     ^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/template.vala:455.16-455.46: warning: unhandled error `GLib.Error'
		while((tmp = in_stream.read_line(null, null)) != null)
		             ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/template.vala:68.11-68.60: warning: unhandled error `GLib.RegexError'
		nicks = new Regex("(^|\\s|['\"+&!/\\(-])@([A-Za-z0-9_]+)");
		        ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/template.vala:69.10-69.81: warning: unhandled error `GLib.RegexError'
		tags = new Regex("(^|\\s|['\"+&!/\\(-])#([A-Za-z0-9_.-\\p{Latin}\\p{Greek}]+)");
		       ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/template.vala:70.12-70.61: warning: unhandled error `GLib.RegexError'
		groups = new Regex("(^|\\s|['\"+&!/\\(-])!([A-Za-z0-9_]+)"); //for identi.ca groups
		         ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/template.vala:71.10-71.94: warning: unhandled error `GLib.RegexError'
		urls = new Regex("((https?|ftp)://([A-Za-z0-9+&@#/%?=~_|!:,.;-]*)([A-Za-z0-9+&@#/%=~_|$]))"); // still needs to be improved for urls containing () such as wikipedia's
		       ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/template.vala:74.18-74.50: warning: unhandled error `GLib.RegexError'
		clear_notice = new Regex("[: \n\t\r&#9851;&#9850;]+|@[^ ]+");
		               ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/template.vala:377.14-377.41: warning: unhandled error `GLib.RegexError'
			var pat = new Regex("{{" + key + "}}");
			          ^^^^^^^^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/template.vala:378.13-378.48: warning: unhandled error `GLib.RegexError'
			result = pat.replace(result, -1, 0, map[key]);
			         ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/template.vala:393.17-393.100: warning: unhandled error `GLib.RegexError'
			bool bingo = urls.match_all_full(text, -1, pos, GLib.RegexMatchFlags.NEWLINE_ANY, out match_info);
			             ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/template.vala:408.12-408.95: warning: unhandled error `GLib.RegexError'
		result = nicks.replace(result, -1, 0, "\\1@<a class='re_nick' href='userinfo://\\2'>\\2</a>");
		         ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/template.vala:410.12-410.101: warning: unhandled error `GLib.RegexError'
		result = tags.replace(result, -1, 0, "\\1#<a class='tags' href='%s\\2'>\\2</a>".printf(search_url));
		         ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/template.vala:413.13-413.106: warning: unhandled error `GLib.RegexError'
			result = groups.replace(result, -1, 0, "\\1!<a class='tags' href='http://identi.ca/group/\\2'>\\2</a>");
			         ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/template.vala:219.34-219.70: warning: unhandled error `GLib.RegexError'
			if(prefs.rtlSupport && is_rtl(clear_notice.replace(text, -1, 0, "")))
			                              ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/template.vala:298.35-298.71: warning: unhandled error `GLib.RegexError'
				if(prefs.rtlSupport && is_rtl(clear_notice.replace(text, -1, 0, "")))
				                              ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/template.vala:351.35-351.71: warning: unhandled error `GLib.RegexError'
				if(prefs.rtlSupport && is_rtl(clear_notice.replace(text, -1, 0, "")))
				                              ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/timeline_list_abstract.vala:62.2-62.24: warning: TimelineListAbstract.parent hides inherited field `Gtk.Widget.parent'. Use the `new' keyword if hiding was intentional
	protected Window parent;
	^^^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/status_bar_smart.vala:73.31-73.74: warning: unhandled error `GLib.Error'
		Gdk.PixbufAnimation anima = new Gdk.PixbufAnimation.from_file(icon_path);
		                            ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/status_view_dialog.vala:43.31-43.85: warning: unhandled error `GLib.Error'
		Gdk.PixbufAnimation anima = new Gdk.PixbufAnimation.from_file(Config.PROGRESS_PATH);
		                            ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/timeline_list_abstract.vala:276.4-277.54: warning: unhandled error `GLib.SpawnError'
/home/ariel/Escritorio/pino-twitter/src/popups.vala:99.3-99.14: warning: unhandled error `GLib.Error'
		popup.show();
		^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/popups.vala:86.31-86.63: warning: unhandled error `GLib.Error'
			popup.set_icon_from_pixbuf(new Gdk.Pixbuf.from_file(av_path));
			                           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/popups.vala:90.3-90.14: warning: unhandled error `GLib.Error'
		popup.show();
		^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/main_window.vala:73.2-73.22: warning: MainWindow.notify hides inherited field `GLib.Object.notify'. Use the `new' keyword if hiding was intentional
	private Popups notify;
	^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/favorites_view_dialog.vala:95.33-95.87: warning: unhandled error `GLib.Error'
				Gdk.PixbufAnimation anima = new Gdk.PixbufAnimation.from_file(Config.PROGRESS_PATH);
				                            ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/favorites_view_dialog.vala:41.31-41.85: warning: unhandled error `GLib.Error'
		Gdk.PixbufAnimation anima = new Gdk.PixbufAnimation.from_file(Config.PROGRESS_PATH);
		                            ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/account_widget.vala:34.2-34.22: warning: AccountWidget.parent hides inherited field `Gtk.Widget.parent'. Use the `new' keyword if hiding was intentional
	private Window parent;
	^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/edit_account.vala:27.2-27.22: warning: EditAccount.parent hides inherited field `Gtk.Widget.parent'. Use the `new' keyword if hiding was intentional
	private Window parent;
	^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/account_widget.vala:155.2-155.26: warning: AccountWidget.delete_event hides inherited method `Gtk.Widget.delete_event'. Use the `new' keyword if hiding was intentional
	private void delete_event() {
	^^^^^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/pref_dialog.vala:166.5-168.55: warning: unhandled error `GLib.SpawnError'
/home/ariel/Escritorio/pino-twitter/src/color_utils.vala:48.14-48.86: warning: unhandled error `GLib.RegexError'
		Regex re = new Regex("rgba\\(([0-9]+), ([0-9]+), ([0-9]+), ([0-9]\\.[0-9][0-9])\\)");
		           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/color_utils.vala:49.23-49.52: warning: unhandled error `GLib.RegexError'
		color.red = (uint16)re.replace(rgba, -1, 0, "\\1").to_int() * 256;
		                    ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/color_utils.vala:50.25-50.54: warning: unhandled error `GLib.RegexError'
		color.green = (uint16)re.replace(rgba, -1, 0, "\\2").to_int() * 256;
		                      ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/color_utils.vala:51.24-51.53: warning: unhandled error `GLib.RegexError'
		color.blue = (uint16)re.replace(rgba, -1, 0, "\\3").to_int() * 256;
		                     ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/color_utils.vala:52.20-52.49: warning: unhandled error `GLib.RegexError'
		alpha = (uint16)(re.replace(rgba, -1, 0, "\\4").to_double() * 256.0 * 256.0);
		                 ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/main_window.vala:460.29-460.73: warning: unhandled error `GLib.Error'
		createDirectAct.set_gicon(Icon.new_for_string(Config.DIRECT_REPLY_PATH));
		                          ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/main_window.vala:474.30-474.70: warning: unhandled error `GLib.Error'
		showFavoritesAct.set_gicon(Icon.new_for_string(Config.FAVORITE_PATH));
		                           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/main_window.vala:626.3-626.50: warning: unhandled error `GLib.Error'
		ui.add_ui_from_string(uiString, uiString.length);
		^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/main_window.vala:79.10-79.51: warning: unhandled error `GLib.Error'
		logo = new Gdk.Pixbuf.from_file(Config.LOGO_PATH);
		       ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/main_window.vala:80.16-80.63: warning: unhandled error `GLib.Error'
		logo_fresh = new Gdk.Pixbuf.from_file(Config.LOGO_FRESH_PATH);
		             ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/main_window.vala:190.4-190.44: warning: unhandled error `GLib.Error'
			Icon.new_for_string(Config.TIMELINE_PATH),
			^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/main_window.vala:191.4-191.50: warning: unhandled error `GLib.Error'
			Icon.new_for_string(Config.TIMELINE_FRESH_PATH), "HomeAct", _("Home timeline"),
			^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/main_window.vala:197.4-197.44: warning: unhandled error `GLib.Error'
			Icon.new_for_string(Config.MENTIONS_PATH),
			^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/main_window.vala:198.4-198.50: warning: unhandled error `GLib.Error'
			Icon.new_for_string(Config.MENTIONS_FRESH_PATH), "MentionsAct", _("Mentions"),
			^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/main_window.vala:204.4-204.42: warning: unhandled error `GLib.Error'
			Icon.new_for_string(Config.DIRECT_PATH),
			^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/main_window.vala:205.4-205.48: warning: unhandled error `GLib.Error'
			Icon.new_for_string(Config.DIRECT_FRESH_PATH), "DirectAct", _("Direct messages"),
			^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/main_window.vala:210.4-210.43: warning: unhandled error `GLib.Error'
			Icon.new_for_string(Config.USERPIC_PATH), prefs.nativeLinkColor,
			^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/tray_icon.vala:52.11-52.26: warning: unhandled error `GLib.Error'
			logo = info.load_icon();
			       ^^^^^^^^^^^^^^^^
/home/ariel/Escritorio/pino-twitter/src/tray_icon.vala:60.17-60.32: warning: unhandled error `GLib.Error'
			logo_fresh = info.load_icon();
			             ^^^^^^^^^^^^^^^^
Compilation failed: 2 error(s), 90 warning(s)
make[2]: *** [src/rest_api_timeline.c] Error 1
make[1]: *** [CMakeFiles/pino.dir/all] Error 2
make: *** [all] Error 2
ariel@ariel-A770M-A:~/Escritorio/pino-twitter/build$ 

```

ojala alguien me pueda ayudar

---

### Post by moreback on 2011-01-10
¿Tienes las herramientas de Vala para compilar ese código?

---

### Post by 3nG3ndR0 on 2011-01-10
si esta instalado

bueno encontré una ppa para maverick así que instale pino y funciona de lujo

```
sudo apt-add-repositoryppa:popey/pino
sudo apt-get update
sudo apt-get install pino
```

---

