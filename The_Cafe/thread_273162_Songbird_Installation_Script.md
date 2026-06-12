---
title: "Songbird Installation Script"
date: 2006-10-07
forum: The Cafe
---

### Post by aysiu on 2006-10-07
I just created an installation script for Songbird 0.2, in case anyone's interested.

The instructions and script can be found here:
[http://www.psychocats.net/ubuntu/songbird](http://www.psychocats.net/ubuntu/songbird)

The script is for x86, not AMD64.

---

### Post by GStubbs43 on 2006-10-07
Why not in the Howto section aysiu? I'm trying it right now. I've used Songbird before and was just thinking this morning someone should make a script for it! :D

---

### Post by aysiu on 2006-10-07
I tested it only once, and it appeared to work for my computer. If you notice anything wrong with it, let me know, and I'll fix it.

---

### Post by GStubbs43 on 2006-10-07
nope... everything works fine on my computer, on a fresh Ubuntu install.

---

### Post by _lynX on 2006-10-07
> **aysiu said:**
> I just created an installation script for Songbird 0.2, in case anyone's interested.

The instructions and script can be found here:
[http://www.psychocats.net/ubuntu/songbird](http://www.psychocats.net/ubuntu/songbird)

Thanks for the script aysiu!

---

### Post by croak77 on 2006-10-07
Is Songbird actually worth installing now or wait until it gets closer to 1.0?

---

### Post by fuscia on 2006-10-07
worked great. thanks, aysiu.

---

### Post by catlett on 2006-10-07
Thank you for the script. Just wanted to add to your feedback, it worked without a problem on my system. The only issue I had was my own ignorance, I didn't use capital S when launching. When I looked back at the post, you already took the care to include a reminder about the launcher. Thanks again.

---

### Post by aysiu on 2006-10-07
> **croak77 said:**
> Is Songbird actually worth installing now or wait until it gets closer to 1.0?
0.1 was still very crash-prone, but 0.2 seems better.

Still, it is beta software... or alpha, some might argue.

[quote=catlett]The only issue I had was my own ignorance, I didn't use capital S when launching. When I looked back at the post, you already took the care to include a reminder about the launcher. Thanks again.[/quote] Actually, does anyone know a solution to this? When I try to symlink the launcher to /usr/bin/songbird, it complains about the application.ini file missing. If I symlink it to /usr/bin/Songbird, it works just fine.

I'd really much rather have it be lowercase. Any programming gurus out there know an easy solution?

By the way, if the script worked correctly, it should have a songbird.desktop file in /usr/share/applications, so theoretically, you shouldn't have to add a launcher if you refresh your menus.

Anyone finding that to be the case?

---

### Post by RAV TUX on 2006-10-07
> **aysiu said:**
> 0.1 was still very crash-prone, but 0.2 seems better.

Still, it is beta software... or alpha, some might argue.

 Actually, does anyone know a solution to this? When I try to symlink the launcher to /usr/bin/songbird, it complains about the application.ini file missing. If I symlink it to /usr/bin/Songbird, it works just fine.

I'd really much rather have it be lowercase. Any programming gurus out there know an easy solution?

By the way, if the script worked correctly, it should have a songbird.desktop file in /usr/share/applications, so theoretically, you shouldn't have to add a launcher if you refresh your menus.

Anyone finding that to be the case?

Aysiu, I know  you wrote the script for Ubuntu but curious as I am I tested it out in Knoppix (Debian installed by Knoppix)

anyway everything seemed to run fine but here is what I got:
```

jozef@knoppixjozef:~/Desktop$ chmod +x installsongbird.sh
jozef@knoppixjozef:~/Desktop$ ./installsongbird.sh
--16:45:48--  [http://download.songbirdnest.com/installer/linux/i686/Songbird_0_2_RC2_linux-i686.tar.gz](http://download.songbirdnest.com/installer/linux/i686/Songbird_0_2_RC2_linux-i686.tar.gz)
           => `Songbird_0_2_RC2_linux-i686.tar.gz'
Resolving download.songbirdnest.com... 82.165.186.187
Connecting to download.songbirdnest.com|82.165.186.187|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 17,850,251 (17M) [application/x-gzip]

100%[====================================>] 17,850,251   159.07K/s    ETA 00:00

16:47:46 (148.04 KB/s) - `Songbird_0_2_RC2_linux-i686.tar.gz' saved [17850251/17850251]

Songbird_20061003/
Songbird_20061003/components/
Songbird_20061003/components/sbGStreamer.xpt
Songbird_20061003/components/sbDeviceManager.so
Songbird_20061003/components/sbUSBMassStorageDevice.xpt
Songbird_20061003/components/sbWMDevice.xpt
Songbird_20061003/components/sbDataRemote.js
Songbird_20061003/components/sbPlaylistPlayback.js
Songbird_20061003/components/sbPlaylistWriterXSPF.js
Songbird_20061003/components/sbPlaylistsource.so
Songbird_20061003/components/sbMetadataHandlerOGG.so
Songbird_20061003/components/sbPlaylistReaderRDF.js
Songbird_20061003/components/sbPlaylistManager.js
Songbird_20061003/components/sbMediaLibrary.so
Songbird_20061003/components/sbUSBMassStorageDevice.so
Songbird_20061003/components/sbMetadataHandlerMP4.so
Songbird_20061003/components/sbMediaLibrary.xpt
Songbird_20061003/components/sbPlaylistReaderListener.js
Songbird_20061003/components/sbServicesource.so
Songbird_20061003/components/sbIntegration.xpt
Songbird_20061003/components/sbCDDevice.xpt
Songbird_20061003/components/sbDownloadDevice.xpt
Songbird_20061003/components/sbPlaylistsource.xpt
Songbird_20061003/components/sbSimplePlaylist.js
Songbird_20061003/components/sbPlaylistWriterManager.js
Songbird_20061003/components/sbGStreamer.so
Songbird_20061003/components/sbPlaylistReaderHTML.js
Songbird_20061003/components/sbServicesource.xpt
Songbird_20061003/components/sbPlaylistReaderAtom.js
Songbird_20061003/components/sbPlaylistPlayback.xpt
Songbird_20061003/components/sbDeviceManager.xpt
Songbird_20061003/components/sbBundle.js
Songbird_20061003/components/sbMediaLibrary.js
Songbird_20061003/components/sbPlaylistReaderM3U.so
Songbird_20061003/components/sbMetadataHandlerID3.so
Songbird_20061003/components/sbMetadataManager.so
Songbird_20061003/components/sbMetadataManager.xpt
Songbird_20061003/components/sbWindowCloak.js
Songbird_20061003/components/sbBundle.xpt
Songbird_20061003/components/sbPlaylistReaderManager.js
Songbird_20061003/components/sbDeviceBase.xpt
Songbird_20061003/components/sbDownloadDevice.so
Songbird_20061003/components/sbPlaylistReaderPLS.so
Songbird_20061003/components/sbPlaylistModule.js
Songbird_20061003/components/sbHotkeyActions.js
Songbird_20061003/components/sbDataRemote.xpt
Songbird_20061003/components/sbMetrics.xpt
Songbird_20061003/components/flashplayer.xpt
Songbird_20061003/components/sbMetrics.js
Songbird_20061003/components/sbPlaylistReaderRSS.js
Songbird_20061003/vlcplugins/
Songbird_20061003/gpl.txt
Songbird_20061003/application.ini
Songbird_20061003/xulrunner/
Songbird_20061003/xulrunner/xulrunner-bin
Songbird_20061003/xulrunner/xpicleanup
Songbird_20061003/xulrunner/LICENSE
Songbird_20061003/xulrunner/components/
Songbird_20061003/xulrunner/components/appshell.xpt
Songbird_20061003/xulrunner/components/dom_xbl.xpt
Songbird_20061003/xulrunner/components/jsconsole.xpt
Songbird_20061003/xulrunner/components/dom.xpt
Songbird_20061003/xulrunner/components/feeds.xpt
Songbird_20061003/xulrunner/components/storage.xpt
Songbird_20061003/xulrunner/components/dom_core.xpt
Songbird_20061003/xulrunner/components/content_html.xpt
Songbird_20061003/xulrunner/components/pipnss.xpt
Songbird_20061003/xulrunner/components/necko_data.xpt
Songbird_20061003/xulrunner/components/caps.xpt
Songbird_20061003/xulrunner/components/content_xtf.xpt
Songbird_20061003/xulrunner/components/layout_base.xpt
Songbird_20061003/xulrunner/components/saxparser.xpt
Songbird_20061003/xulrunner/components/libpippki.so
Songbird_20061003/xulrunner/components/necko_strconv.xpt
Songbird_20061003/xulrunner/components/mozgnome.xpt
Songbird_20061003/xulrunner/components/xpcom_io.xpt
Songbird_20061003/xulrunner/components/dom_range.xpt
Songbird_20061003/xulrunner/components/commandlines.xpt
Songbird_20061003/xulrunner/components/uriloader.xpt
Songbird_20061003/xulrunner/components/necko_http.xpt
Songbird_20061003/xulrunner/components/necko_file.xpt
Songbird_20061003/xulrunner/components/toolkitprofile.xpt
Songbird_20061003/xulrunner/components/necko_socket.xpt
Songbird_20061003/xulrunner/components/downloads.xpt
Songbird_20061003/xulrunner/components/webshell_idls.xpt
Songbird_20061003/xulrunner/components/dom_xpath.xpt
Songbird_20061003/xulrunner/components/necko_ftp.xpt
Songbird_20061003/xulrunner/components/chardet.xpt
Songbird_20061003/xulrunner/components/toolkitremote.xpt
Songbird_20061003/xulrunner/components/dom_loadsave.xpt
Songbird_20061003/xulrunner/components/htmlparser.xpt
Songbird_20061003/xulrunner/components/necko_cookie.xpt
Songbird_20061003/xulrunner/components/pipboot.xpt
Songbird_20061003/xulrunner/components/nsCloseAllWindows.js
Songbird_20061003/xulrunner/components/websrvcs.xpt
Songbird_20061003/xulrunner/components/gfx.xpt
Songbird_20061003/xulrunner/components/directory.xpt
Songbird_20061003/xulrunner/components/progressDlg.xpt
Songbird_20061003/xulrunner/components/satchel.xpt
Songbird_20061003/xulrunner/components/proxyObjInst.xpt
Songbird_20061003/xulrunner/components/xpcom_base.xpt
Songbird_20061003/xulrunner/components/xultmpl.xpt
Songbird_20061003/xulrunner/components/fastfind.xpt
Songbird_20061003/xulrunner/components/layout_xul_tree.xpt
Songbird_20061003/xulrunner/components/windowwatcher.xpt
Songbird_20061003/xulrunner/components/nsFilePicker.js
Songbird_20061003/xulrunner/components/exthandler.xpt
Songbird_20061003/xulrunner/components/oji.xpt
Songbird_20061003/xulrunner/components/pippki.xpt
Songbird_20061003/xulrunner/components/nsUpdateService.js
Songbird_20061003/xulrunner/components/plugin.xpt
Songbird_20061003/xulrunner/components/xulapp.xpt
Songbird_20061003/xulrunner/components/shistory.xpt
Songbird_20061003/xulrunner/components/libmozgnome.so
Songbird_20061003/xulrunner/components/dom_storage.xpt
Songbird_20061003/xulrunner/components/prefetch.xpt
Songbird_20061003/xulrunner/components/libpipnss.so
Songbird_20061003/xulrunner/components/nsHelperAppDlg.js
Songbird_20061003/xulrunner/components/alerts.xpt
Songbird_20061003/xulrunner/components/dom_xul.xpt
Songbird_20061003/xulrunner/components/venkman-service.js
Songbird_20061003/xulrunner/components/libnkgnomevfs.so
Songbird_20061003/xulrunner/components/commandhandler.xpt
Songbird_20061003/xulrunner/components/jar.xpt
Songbird_20061003/xulrunner/components/dom_events.xpt
Songbird_20061003/xulrunner/components/nsDefaultCLH.js
Songbird_20061003/xulrunner/components/libfileview.so
Songbird_20061003/xulrunner/components/chrome.xpt
Songbird_20061003/xulrunner/components/dom_sidebar.xpt
Songbird_20061003/xulrunner/components/editor.xpt
Songbird_20061003/xulrunner/components/embed_base.xpt
Songbird_20061003/xulrunner/components/windowds.xpt
Songbird_20061003/xulrunner/components/content_htmldoc.xpt
Songbird_20061003/xulrunner/components/accessibility-atk.xpt
Songbird_20061003/xulrunner/components/dom_views.xpt
Songbird_20061003/xulrunner/components/mozfind.xpt
Songbird_20061003/xulrunner/components/libsystem-pref.so
Songbird_20061003/xulrunner/components/nsExtensionManager.js
Songbird_20061003/xulrunner/components/content_base.xpt
Songbird_20061003/xulrunner/components/xpconnect.xpt
Songbird_20061003/xulrunner/components/xulapp_setup.xpt
Songbird_20061003/xulrunner/components/layout_xul.xpt
Songbird_20061003/xulrunner/components/libpipboot.so
Songbird_20061003/xulrunner/components/history.xpt
Songbird_20061003/xulrunner/components/libwebsrvcs.so
Songbird_20061003/xulrunner/components/libautoconfig.so
Songbird_20061003/xulrunner/components/libxulutil.so
Songbird_20061003/xulrunner/components/necko_about.xpt
Songbird_20061003/xulrunner/components/necko_res.xpt
Songbird_20061003/xulrunner/components/xpcom_threads.xpt
Songbird_20061003/xulrunner/components/dom_base.xpt
Songbird_20061003/xulrunner/components/profile.xpt
Songbird_20061003/xulrunner/components/extensions.xpt
Songbird_20061003/xulrunner/components/xulrunner.xpt
Songbird_20061003/xulrunner/components/webbrowserpersist.xpt
Songbird_20061003/xulrunner/components/txtsvc.xpt
Songbird_20061003/xulrunner/components/FeedProcessor.js
Songbird_20061003/xulrunner/components/nsProxyAutoConfig.js
Songbird_20061003/xulrunner/components/libxmlextras.so
Songbird_20061003/xulrunner/components/dom_canvas.xpt
Songbird_20061003/xulrunner/components/imglib2.xpt
Songbird_20061003/xulrunner/components/nsDictionary.js
Songbird_20061003/xulrunner/components/dom_svg.xpt
Songbird_20061003/xulrunner/components/composer.xpt
Songbird_20061003/xulrunner/components/find.xpt
Songbird_20061003/xulrunner/components/docshell.xpt
Songbird_20061003/xulrunner/components/libimgicon.so
Songbird_20061003/xulrunner/components/dom_html.xpt
Songbird_20061003/xulrunner/components/autocomplete.xpt
Songbird_20061003/xulrunner/components/update.xpt
Songbird_20061003/xulrunner/components/necko_dns.xpt
Songbird_20061003/xulrunner/components/dom_traversal.xpt
Songbird_20061003/xulrunner/components/widget.xpt
Songbird_20061003/xulrunner/components/content_xmldoc.xpt
Songbird_20061003/xulrunner/components/inspector.xpt
Songbird_20061003/xulrunner/components/appstartup.xpt
Songbird_20061003/xulrunner/components/nsXULAppInstall.js
Songbird_20061003/xulrunner/components/nsInterfaceInfoToIDL.js
Songbird_20061003/xulrunner/components/mozbrwsr.xpt
Songbird_20061003/xulrunner/components/jsconsole-clhandler.js
Songbird_20061003/xulrunner/components/necko.xpt
Songbird_20061003/xulrunner/components/dom_stylesheets.xpt
Songbird_20061003/xulrunner/components/xpinstall.xpt
Songbird_20061003/xulrunner/components/imgicon.xpt
Songbird_20061003/xulrunner/components/mimetype.xpt
Songbird_20061003/xulrunner/components/layout_printing.xpt
Songbird_20061003/xulrunner/components/urlformatter.xpt
Songbird_20061003/xulrunner/components/autoconfig.xpt
Songbird_20061003/xulrunner/components/xpcom_components.xpt
Songbird_20061003/xulrunner/components/rdf.xpt
Songbird_20061003/xulrunner/components/necko_viewsource.xpt
Songbird_20061003/xulrunner/components/passwordmgr.xpt
Songbird_20061003/xulrunner/components/filepicker.xpt
Songbird_20061003/xulrunner/components/content_xslt.xpt
Songbird_20061003/xulrunner/components/lwbrk.xpt
Songbird_20061003/xulrunner/components/intl.xpt
Songbird_20061003/xulrunner/components/xml-rpc.xpt
Songbird_20061003/xulrunner/components/txmgr.xpt
Songbird_20061003/xulrunner/components/xpcom_xpti.xpt
Songbird_20061003/xulrunner/components/nsResetPref.js
Songbird_20061003/xulrunner/components/nsXmlRpcClient.js
Songbird_20061003/xulrunner/components/necko_cache.xpt
Songbird_20061003/xulrunner/components/gksvgrenderer.xpt
Songbird_20061003/xulrunner/components/webBrowser_core.xpt
Songbird_20061003/xulrunner/components/nsProgressDialog.js
Songbird_20061003/xulrunner/components/locale.xpt
Songbird_20061003/xulrunner/components/xuldoc.xpt
Songbird_20061003/xulrunner/components/pref.xpt
Songbird_20061003/xulrunner/components/dom_css.xpt
Songbird_20061003/xulrunner/components/libauth.so
Songbird_20061003/xulrunner/components/xpcom_obsolete.xpt
Songbird_20061003/xulrunner/components/libuniversalchardet.so
Songbird_20061003/xulrunner/components/accessibility.xpt
Songbird_20061003/xulrunner/components/uconv.xpt
Songbird_20061003/xulrunner/components/jsdservice.xpt
Songbird_20061003/xulrunner/components/xpcom_ds.xpt
Songbird_20061003/xulrunner/components/nsKillAll.js
Songbird_20061003/xulrunner/components/libtransformiix.so
Songbird_20061003/xulrunner/components/unicharutil.xpt
Songbird_20061003/xulrunner/components/nsURLFormatter.js
Songbird_20061003/xulrunner/extensions/
Songbird_20061003/xulrunner/extensions/rubberducky@songbirdnest.com/
Songbird_20061003/xulrunner/extensions/rubberducky@songbirdnest.com/chrome.manifest
Songbird_20061003/xulrunner/extensions/rubberducky@songbirdnest.com/install.rdf
Songbird_20061003/xulrunner/extensions/inspector@mozilla.org/
Songbird_20061003/xulrunner/extensions/inspector@mozilla.org/components/
Songbird_20061003/xulrunner/extensions/inspector@mozilla.org/components/inspector-cmdline.js
Songbird_20061003/xulrunner/extensions/inspector@mozilla.org/chrome.manifest
Songbird_20061003/xulrunner/extensions/inspector@mozilla.org/defaults/
Songbird_20061003/xulrunner/extensions/inspector@mozilla.org/defaults/preferences/
Songbird_20061003/xulrunner/extensions/inspector@mozilla.org/defaults/preferences/inspector.js
Songbird_20061003/xulrunner/extensions/inspector@mozilla.org/install.rdf
Songbird_20061003/xulrunner/extensions/inspector@mozilla.org/chrome/
Songbird_20061003/xulrunner/extensions/inspector@mozilla.org/chrome/chromelist.txt
Songbird_20061003/xulrunner/extensions/inspector@mozilla.org/chrome/inspector.jar
Songbird_20061003/xulrunner/extensions/dove@songbirdnest.com/
Songbird_20061003/xulrunner/extensions/dove@songbirdnest.com/chrome.manifest
Songbird_20061003/xulrunner/extensions/dove@songbirdnest.com/dove.jar
Songbird_20061003/xulrunner/extensions/dove@songbirdnest.com/install.rdf
Songbird_20061003/xulrunner/libsmime3.so
Songbird_20061003/xulrunner/dependentlibs.list
Songbird_20061003/xulrunner/libid3-3.8.so.3.0.0
Songbird_20061003/xulrunner/libfreebl3.chk
Songbird_20061003/xulrunner/mozilla-xremote-client
Songbird_20061003/xulrunner/bloaturls.txt
Songbird_20061003/xulrunner/regxpcom
Songbird_20061003/xulrunner/libplds4.so
Songbird_20061003/xulrunner/icons/
Songbird_20061003/xulrunner/icons/document.png
Songbird_20061003/xulrunner/icons/mozicon16.xpm
Songbird_20061003/xulrunner/icons/mozicon50.xpm
Songbird_20061003/xulrunner/libxul.so
Songbird_20061003/xulrunner/libid3-3.8.so.3
Songbird_20061003/xulrunner/shlibsign
Songbird_20061003/xulrunner/updater
Songbird_20061003/xulrunner/libsoftokn3.chk
Songbird_20061003/xulrunner/xpidl
Songbird_20061003/xulrunner/libplc4.so
Songbird_20061003/xulrunner/xpt_dump
Songbird_20061003/xulrunner/libgtkembedmoz.so
Songbird_20061003/xulrunner/xulrunner-config
Songbird_20061003/xulrunner/xulrunner
Songbird_20061003/xulrunner/elf-dynstr-gc
Songbird_20061003/xulrunner/libnss3.so
Songbird_20061003/xulrunner/greprefs/
Songbird_20061003/xulrunner/greprefs/all.js
Songbird_20061003/xulrunner/greprefs/security-prefs.js
Songbird_20061003/xulrunner/greprefs/xpinstall.js
Songbird_20061003/xulrunner/nsinstall
Songbird_20061003/xulrunner/libfreebl3.so
Songbird_20061003/xulrunner/mozilla-installer-bin
Songbird_20061003/xulrunner/defaults/
Songbird_20061003/xulrunner/defaults/pref/
Songbird_20061003/xulrunner/defaults/pref/xulrunner.js
Songbird_20061003/xulrunner/defaults/autoconfig/
Songbird_20061003/xulrunner/defaults/autoconfig/prefcalls.js
Songbird_20061003/xulrunner/defaults/autoconfig/platform.js
Songbird_20061003/xulrunner/defaults/profile/
Songbird_20061003/xulrunner/defaults/profile/US/
Songbird_20061003/xulrunner/defaults/profile/US/chrome/
Songbird_20061003/xulrunner/defaults/profile/US/chrome/userChrome-example.css
Songbird_20061003/xulrunner/defaults/profile/US/chrome/userContent-example.css
Songbird_20061003/xulrunner/defaults/profile/US/localstore.rdf
Songbird_20061003/xulrunner/defaults/profile/chrome/
Songbird_20061003/xulrunner/defaults/profile/chrome/userChrome-example.css
Songbird_20061003/xulrunner/defaults/profile/chrome/userContent-example.css
Songbird_20061003/xulrunner/defaults/profile/localstore.rdf
Songbird_20061003/xulrunner/libssl3.so
Songbird_20061003/xulrunner/updater.ini
Songbird_20061003/xulrunner/res/
Songbird_20061003/xulrunner/res/table-add-column-after-active.gif
Songbird_20061003/xulrunner/res/table-add-column-before-hover.gif
Songbird_20061003/xulrunner/res/table-add-row-before-active.gif
Songbird_20061003/xulrunner/res/forms.css
Songbird_20061003/xulrunner/res/EditorOverride.css
Songbird_20061003/xulrunner/res/table-remove-row-active.gif
Songbird_20061003/xulrunner/res/charsetalias.properties
Songbird_20061003/xulrunner/res/arrow.gif
Songbird_20061003/xulrunner/res/html/
Songbird_20061003/xulrunner/res/html/gopher-telnet.gif
Songbird_20061003/xulrunner/res/html/gopher-find.gif
Songbird_20061003/xulrunner/res/html/gopher-menu.gif
Songbird_20061003/xulrunner/res/html/gopher-unknown.gif
Songbird_20061003/xulrunner/res/html/gopher-text.gif
Songbird_20061003/xulrunner/res/html/gopher-sound.gif
Songbird_20061003/xulrunner/res/html/gopher-image.gif
Songbird_20061003/xulrunner/res/html/gopher-audio.gif
Songbird_20061003/xulrunner/res/html/gopher-binary.gif
Songbird_20061003/xulrunner/res/html/gopher-movie.gif
Songbird_20061003/xulrunner/res/svg.css
Songbird_20061003/xulrunner/res/fonts/
Songbird_20061003/xulrunner/res/fonts/mathfontSymbol.properties
Songbird_20061003/xulrunner/res/fonts/mathfontPUA.properties
Songbird_20061003/xulrunner/res/fonts/mathfontMath4.properties
Songbird_20061003/xulrunner/res/fonts/mathfontCMSY10.properties
Songbird_20061003/xulrunner/res/fonts/mathfontMath2.properties
Songbird_20061003/xulrunner/res/fonts/mathfontMath1.properties
Songbird_20061003/xulrunner/res/fonts/pangoFontEncoding.properties
Songbird_20061003/xulrunner/res/fonts/fontEncoding.properties
Songbird_20061003/xulrunner/res/fonts/mathfontCMEX10.properties
Songbird_20061003/xulrunner/res/fonts/mathfontMTExtra.properties
Songbird_20061003/xulrunner/res/fonts/mathfont.properties
Songbird_20061003/xulrunner/res/langGroups.properties
Songbird_20061003/xulrunner/res/charsetData.properties
Songbird_20061003/xulrunner/res/cmessage.txt
Songbird_20061003/xulrunner/res/table-remove-row-hover.gif
Songbird_20061003/xulrunner/res/table-remove-column-hover.gif
Songbird_20061003/xulrunner/res/table-add-column-after.gif
Songbird_20061003/xulrunner/res/sample.unixpsfonts.properties
Songbird_20061003/xulrunner/res/table-add-row-after-active.gif
Songbird_20061003/xulrunner/res/table-add-row-after.gif
Songbird_20061003/xulrunner/res/table-add-row-after-hover.gif
Songbird_20061003/xulrunner/res/grabber.gif
Songbird_20061003/xulrunner/res/language.properties
Songbird_20061003/xulrunner/res/table-add-row-before.gif
Songbird_20061003/xulrunner/res/table-add-column-after-hover.gif
Songbird_20061003/xulrunner/res/bloatcycle.html
Songbird_20061003/xulrunner/res/viewer.properties
Songbird_20061003/xulrunner/res/entityTables/
Songbird_20061003/xulrunner/res/entityTables/html40Latin1.properties
Songbird_20061003/xulrunner/res/entityTables/transliterate.properties
Songbird_20061003/xulrunner/res/entityTables/mathml20.properties
Songbird_20061003/xulrunner/res/entityTables/html40Special.properties
Songbird_20061003/xulrunner/res/entityTables/htmlEntityVersions.properties
Songbird_20061003/xulrunner/res/entityTables/html40Symbols.properties
Songbird_20061003/xulrunner/res/samples/
Songbird_20061003/xulrunner/res/samples/treeTest1.css
Songbird_20061003/xulrunner/res/samples/test1.html
Songbird_20061003/xulrunner/res/samples/test6.html
Songbird_20061003/xulrunner/res/samples/test_pr.html
Songbird_20061003/xulrunner/res/samples/printsetup.html
Songbird_20061003/xulrunner/res/samples/test14.html
Songbird_20061003/xulrunner/res/samples/bg.jpg
Songbird_20061003/xulrunner/res/samples/image_props.html
Songbird_20061003/xulrunner/res/samples/test_lbox.html
Songbird_20061003/xulrunner/res/samples/Anieyes.gif
Songbird_20061003/xulrunner/res/samples/test2.html
Songbird_20061003/xulrunner/res/samples/test5.html
Songbird_20061003/xulrunner/res/samples/test10.html
Songbird_20061003/xulrunner/res/samples/toolbarTest1.xul
Songbird_20061003/xulrunner/res/samples/test3.html
Songbird_20061003/xulrunner/res/samples/test8-1.html
Songbird_20061003/xulrunner/res/samples/sliderTest1.xul
Songbird_20061003/xulrunner/res/samples/raptor.jpg
Songbird_20061003/xulrunner/res/samples/test7.html
Songbird_20061003/xulrunner/res/samples/gear1.gif
Songbird_20061003/xulrunner/res/samples/treeTest1.xul
Songbird_20061003/xulrunner/res/samples/test15.html
Songbird_20061003/xulrunner/res/samples/test8tab.html
Songbird_20061003/xulrunner/res/samples/scrollbarTest2.xul
Songbird_20061003/xulrunner/res/samples/test_gfx.html
Songbird_20061003/xulrunner/res/samples/test_ed.html
Songbird_20061003/xulrunner/res/samples/test_form.html
Songbird_20061003/xulrunner/res/samples/test0.html
Songbird_20061003/xulrunner/res/samples/test16.html
Songbird_20061003/xulrunner/res/samples/cform.css
Songbird_20061003/xulrunner/res/samples/find.html
Songbird_20061003/xulrunner/res/samples/checkboxTest.xul
Songbird_20061003/xulrunner/res/samples/test13.html
Songbird_20061003/xulrunner/res/samples/test.wav
Songbird_20061003/xulrunner/res/samples/xulTest.css
Songbird_20061003/xulrunner/res/samples/test9b.html
Songbird_20061003/xulrunner/res/samples/bform.css
Songbird_20061003/xulrunner/res/samples/scrollbarTest1.xul
Songbird_20061003/xulrunner/res/samples/test8.html
Songbird_20061003/xulrunner/res/samples/mozform.css
Songbird_20061003/xulrunner/res/samples/test_weight.html
Songbird_20061003/xulrunner/res/samples/demoform.css
Songbird_20061003/xulrunner/res/samples/test8siz.html
Songbird_20061003/xulrunner/res/samples/test12.html
Songbird_20061003/xulrunner/res/samples/rock_gra.gif
Songbird_20061003/xulrunner/res/samples/soundtest.html
Songbird_20061003/xulrunner/res/samples/test11.html
Songbird_20061003/xulrunner/res/samples/test9a.html
Songbird_20061003/xulrunner/res/samples/test8dom.html
Songbird_20061003/xulrunner/res/samples/beeptest.html
Songbird_20061003/xulrunner/res/samples/aform.css
Songbird_20061003/xulrunner/res/samples/test9.html
Songbird_20061003/xulrunner/res/samples/test4.html
Songbird_20061003/xulrunner/res/samples/test8sca.html
Songbird_20061003/xulrunner/res/table-add-column-before.gif
Songbird_20061003/xulrunner/res/arrowd.gif
Songbird_20061003/xulrunner/res/quirk.css
Songbird_20061003/xulrunner/res/throbber/
Songbird_20061003/xulrunner/res/throbber/anims27.gif
Songbird_20061003/xulrunner/res/throbber/anims24.gif
Songbird_20061003/xulrunner/res/throbber/anims09.gif
Songbird_20061003/xulrunner/res/throbber/anims28.gif
Songbird_20061003/xulrunner/res/throbber/anims18.gif
Songbird_20061003/xulrunner/res/throbber/anims03.gif
Songbird_20061003/xulrunner/res/throbber/anim.gif
Songbird_20061003/xulrunner/res/throbber/anims21.gif
Songbird_20061003/xulrunner/res/throbber/anims15.gif
Songbird_20061003/xulrunner/res/throbber/anims04.gif
Songbird_20061003/xulrunner/res/throbber/anims08.gif
Songbird_20061003/xulrunner/res/throbber/anims20.gif
Songbird_20061003/xulrunner/res/throbber/anims11.gif
Songbird_20061003/xulrunner/res/throbber/anims22.gif
Songbird_20061003/xulrunner/res/throbber/anims29.gif
Songbird_20061003/xulrunner/res/throbber/anims12.gif
Songbird_20061003/xulrunner/res/throbber/anims19.gif
Songbird_20061003/xulrunner/res/throbber/anims14.gif
Songbird_20061003/xulrunner/res/throbber/anims00.gif
Songbird_20061003/xulrunner/res/throbber/anims01.gif
Songbird_20061003/xulrunner/res/throbber/anims25.gif
Songbird_20061003/xulrunner/res/throbber/anims23.gif
Songbird_20061003/xulrunner/res/throbber/anims05.gif
Songbird_20061003/xulrunner/res/throbber/anims17.gif
Songbird_20061003/xulrunner/res/throbber/anims13.gif
Songbird_20061003/xulrunner/res/throbber/anims02.gif
Songbird_20061003/xulrunner/res/throbber/anims16.gif
Songbird_20061003/xulrunner/res/throbber/anims06.gif
Songbird_20061003/xulrunner/res/throbber/anims26.gif
Songbird_20061003/xulrunner/res/throbber/anims10.gif
Songbird_20061003/xulrunner/res/throbber/anims07.gif
Songbird_20061003/xulrunner/res/unixcharset.properties
Songbird_20061003/xulrunner/res/viewsource.css
Songbird_20061003/xulrunner/res/mathml.css
Songbird_20061003/xulrunner/res/table-add-row-before-hover.gif
Songbird_20061003/xulrunner/res/loading-image.gif
Songbird_20061003/xulrunner/res/table-remove-column.gif
Songbird_20061003/xulrunner/res/ua.css
Songbird_20061003/xulrunner/res/table-remove-row.gif
Songbird_20061003/xulrunner/res/table-add-column-before-active.gif
Songbird_20061003/xulrunner/res/table-remove-column-active.gif
Songbird_20061003/xulrunner/res/html.css
Songbird_20061003/xulrunner/res/hiddenWindow.html
Songbird_20061003/xulrunner/res/dtd/
Songbird_20061003/xulrunner/res/dtd/xhtml11.dtd
Songbird_20061003/xulrunner/res/dtd/mathml.dtd
Songbird_20061003/xulrunner/res/broken-image.gif
Songbird_20061003/xulrunner/run-mozilla.sh
Songbird_20061003/xulrunner/README.txt
Songbird_20061003/xulrunner/libnspr4.so
Songbird_20061003/xulrunner/libxpcom.so
Songbird_20061003/xulrunner/TestGtkEmbed
Songbird_20061003/xulrunner/chrome/
Songbird_20061003/xulrunner/chrome/comm.manifest
Songbird_20061003/xulrunner/chrome/chromelist.txt
Songbird_20061003/xulrunner/chrome/pippki.jar
Songbird_20061003/xulrunner/chrome/toolkit.jar
Songbird_20061003/xulrunner/chrome/icons/
Songbird_20061003/xulrunner/chrome/icons/default/
Songbird_20061003/xulrunner/chrome/icons/default/default.xpm
Songbird_20061003/xulrunner/chrome/classic.manifest
Songbird_20061003/xulrunner/chrome/en-US.jar
Songbird_20061003/xulrunner/chrome/pippki.manifest
Songbird_20061003/xulrunner/chrome/venkman.jar
Songbird_20061003/xulrunner/chrome/classic.jar
Songbird_20061003/xulrunner/chrome/en-US.manifest
Songbird_20061003/xulrunner/chrome/comm.jar
Songbird_20061003/xulrunner/chrome/toolkit.manifest
Songbird_20061003/xulrunner/chrome/installed-chrome.txt
Songbird_20061003/xulrunner/libid3.so
Songbird_20061003/xulrunner/xpcshell
Songbird_20061003/xulrunner/plugins/
Songbird_20061003/xulrunner/plugins/libnullplugin.so
Songbird_20061003/xulrunner/plugins/libunixprintplugin.so
Songbird_20061003/xulrunner/xpt_link
Songbird_20061003/xulrunner/libnssckbi.so
Songbird_20061003/xulrunner/libmozjs.so
Songbird_20061003/xulrunner/mangle
Songbird_20061003/xulrunner/libsoftokn3.so
Songbird_20061003/defaults/
Songbird_20061003/defaults/preferences/
Songbird_20061003/defaults/preferences/songbird-channel-prefs.js
Songbird_20061003/defaults/preferences/songbird-prefs.js
Songbird_20061003/Songbird
Songbird_20061003/LICENSE.txt
Songbird_20061003/TRADEMARK.txt
Songbird_20061003/chrome/
Songbird_20061003/chrome/rubberducky.manifest
Songbird_20061003/chrome/icons/
Songbird_20061003/chrome/icons/default/
Songbird_20061003/chrome/icons/default/default.xpm
Songbird_20061003/chrome/classic.manifest
Songbird_20061003/chrome/songbird.jar
Songbird_20061003/chrome/locales.manifest
Songbird_20061003/chrome/classic.jar
Songbird_20061003/chrome/locales.jar
Songbird_20061003/chrome/rubberducky.jar
Songbird_20061003/chrome/songbird.manifest
Songbird_20061003/plugins/
Songbird_20061003/plugins/libflashplayer.so
Songbird_20061003/scripts/
Songbird_20061003/scripts/sbPlaylistBase.js
Songbird_20061003/scripts/sbSmartPlaylist.js
Songbird_20061003/scripts/sbDynamicPlaylist.js
Songbird_20061003/scripts/sbPlaylist.js
jozef is not in the sudoers file.  This incident will be reported.
jozef is not in the sudoers file.  This incident will be reported.
--16:47:48--  [http://www.son/](http://www.son/)
           => `index.html'
Resolving [www.son]("http://www.son")... failed: Name or service not known.
--16:47:48--  [http://gbirdnest.com/themes/gespaa_customized/sexy_features.png](http://gbirdnest.com/themes/gespaa_customized/sexy_features.png)
           => `sexy_features.png'
Resolving gbirdnest.com... failed: Name or service not known.

FINISHED --16:47:49--
Downloaded: 0 bytes in 0 files
jozef is not in the sudoers file.  This incident will be reported.
--16:47:49--  [http://www.psychocats.net/ubuntu/songbird.desktop](http://www.psychocats.net/ubuntu/songbird.desktop)
           => `songbird.desktop'
Resolving [www.psychocats.net]("http://www.psychocats.net")... 64.14.68.87
Connecting to www.psychocats.net|64.14.68.87|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 7,467 (7.3K) [text/plain]

100%[====================================>] 7,467         --.--K/s

16:47:49 (118.31 KB/s) - `songbird.desktop' saved [7467/7467]

jozef is not in the sudoers file.  This incident will be reported.
```

---

### Post by RAV TUX on 2006-10-07
and here is what I got so far...

---

### Post by RAV TUX on 2006-10-07
> **yozef said:**
> and here is what I got so far...

well aside from that cumbersome alert message all is good

---

### Post by aysiu on 2006-10-07
> **yozef said:**
> Aysiu, I know  you wrote the script for Ubuntu but curious as I am I tested it out in Knoppix (Debian installed by Knoppix)

anyway everything seemed to run fine but here is what I got: It's definitely designed for Ubuntu and not Knoppix.

```
Resolving www.son... failed: Name or service not known.
--16:47:48-- http://gbirdnest.com/themes/gespaa_c...y_features.png
=> `sexy_features.png'
Resolving gbirdnest.com... failed: Name or service not known.
``` I've fixed this error. I caught it before, but apparently I didn't upload the corrected file. It should be good now (I had a space in the URL I was *wget*ing).

```
jozef is not in the sudoers file. This incident will be reported.
``` This makes sense, too. Knoppix uses root instead of *sudo*.

---

### Post by GStubbs43 on 2006-10-07
Hey, I just noticed something.... It put an icon in the Applications menu, but it has no icon... after the  "sudo mv sexy_features.png /usr/share/pixmaps/songbird.png" it shows "mv: cannot stat `sexy_features.png': No such file or directory"

edit: That's what you just fixed... I was a bit slow on typing. ;)

---

### Post by RAV TUX on 2006-10-07
> **aysiu said:**
> It's definitely designed for Ubuntu and not Knoppix.

```
Resolving www.son... failed: Name or service not known.
--16:47:48-- http://gbirdnest.com/themes/gespaa_c...y_features.png
=> `sexy_features.png'
Resolving gbirdnest.com... failed: Name or service not known.
``` I've fixed this error. I caught it before, but apparently I didn't upload the corrected file. It should be good now (I had a space in the URL I was *wget*ing).

```
jozef is not in the sudoers file. This incident will be reported.
``` This makes sense, too. Knoppix uses root instead of *sudo*.

Thanks Aysiu, I just like to test things out everywhere....

---

### Post by aysiu on 2006-10-07
> **GStubbs43 said:**
> Hey, I just noticed something.... It put an icon in the Applications menu, but it has no icon... after the  "sudo mv sexy_features.png /usr/share/pixmaps/songbird.png" it shows "mv: cannot stat `sexy_features.png': No such file or directory"

edit: That's what you just fixed... I was a bit slow on typing. ;)
That is what I just fixed. Thanks for picking up on it, though.

The line used to read: ```
wget -c http://www.son gbirdnest.com/themes/gespaa_customized/sexy_features.png
``` Now it reads (as it should): ```
wget -c http://www.songbirdnest.com/themes/gespaa_customized/sexy_features.png
```

---

### Post by RAV TUX on 2006-10-07
> **yozef said:**
> Thanks Aysiu, I just like to test things out everywhere....

It's all good with a little hacking got it running great using your script in Knoppix.

(got rid of the pesky error message)

( a bit of 411 ubuntu scripts for the most part work in knoppix, again, actually Debian installed with Knoppix.)

---

### Post by aysiu on 2006-10-07
Do you want to post your Knoppix hack, in case someone else might find it useful?

By the way, I've changed a few things.

There's now a removal script as well, and both scripts (installation and removal) have little narrations to let you know what the script is trying to do.

---

### Post by GStubbs43 on 2006-10-07
> **aysiu said:**
> 
There's now a removal script as well, and both scripts (installation and removal) have little narrations to let you know what the script is trying to do.

How about removing ~/.songbird as well, incase someone messed it up somehow and wants to completly remove it, so they can reinstall it. Also, add directions to chmod +x it as well. ;)

By the way, I'm about to test the removal script and the new install script :-D

---

### Post by aysiu on 2006-10-07
Oh, good point about the directions! I'll do that. Thanks for the suggestion GStubbs43.

I don't want to be too presumptious about deleting people's settings, though...

---

### Post by GStubbs43 on 2006-10-07
Is it possible to add it as an option? Just trying to help here. ;)

---

### Post by GStubbs43 on 2006-10-07
Also, how about this as an icon instead, it has a transparent background, so it doesn't have that white box when highlighted in the menu.

P.S. I just tried both scripts and they work great.

---

### Post by aysiu on 2006-10-07
> **GStubbs43 said:**
> Is it possible to add it as an option? Just trying to help here. ;) Is it possible for a script to exist that gives that option? Yes. Do I know enough about writing scripts to present that option? No.

> **GStubbs43 said:**
> Also, how about this as an icon instead, it has a transparent background, so it doesn't have that white box when highlighted in the menu. I'll work on getting that in. Thanks for providing the icon.

> 
P.S. I just tried both scripts and they work great. And thank for testing!

---

### Post by GStubbs43 on 2006-10-07
> **aysiu said:**
> Is it possible for a script to exist that gives that option? Yes. Do I know enough about writing scripts to present that option? No.

haha, maybe someone can help with that. :rolleyes:

> **aysiu said:**
> 
 I'll work on getting that in. Thanks for providing the icon.

 And thank for testing!


No problem! I see you've already added the icon! 8)

---

### Post by aysiu on 2006-10-07
Yes, I've added the icon, and I've also included instructions for removal, including the removal of the configuration files.

---

### Post by GStubbs43 on 2006-10-07
I didn't see the configuration part when I looked before. Now, I think it is comlplete, but does it say anywhere that it is just a beta software anywhere? You may want to add that.

---

### Post by aysiu on 2006-10-07
> **GStubbs43 said:**
> I didn't see the configuration part when I looked before. Now, I think it is comlplete, but does it say anywhere that it is just a beta software anywhere? You may want to add that. I just added the configuration part (highlighted in red), and I don't use the term *beta*, but I do mention it's version 0.2 (highlighted in green).

---

### Post by GStubbs43 on 2006-10-07
okay, I see it now. ;)

---

### Post by GStubbs43 on 2006-10-07
I have another idea, I think this:
_[IMG]http://www.songbirdnest.com/files/images/button_headphones.png[/IMG]_
would be an even better icon, as it is easier to see and not three little things but just one chubby songbird listening to music. ;) I tried it and it is a lot easier to see in the menu.

---

### Post by ShanghaiTeej on 2006-10-07
The installation worked really well.  Thank you for making this script, i've had my eye on songbird for a long time.  I don't think the icon worked out though, but that doesn't matter, I can make my own.

---

### Post by maniacmusician on 2006-10-07
wow thanks for putting so much effort into this, it was really well thought out! the script worked very nicely. am i right in assuming that you will update the script with newer versions of songbird? thanks again! :)

---

### Post by GStubbs43 on 2006-10-07
> **maniacmusician said:**
> wow thanks for putting so much effort into this, it was really well thought out! the script worked very nicely. am i right in assuming that you will update the script with newer versions of songbird? thanks again! :)


I think Songbird automatically updates itself anyway. I'm not sure if this feature works yet, but since it is based on Firefox, it does have the option, even though it may not work until a final release. :-k

---

### Post by maniacmusician on 2006-10-07
oh i see. It's actually really cpu intensive for me, so i dont think i'm going to stick with it at the moment. didnt know it was based on firefox, that explains the ram consumption lol. it's interesting, i'll be keeping an eye on it.

---

### Post by RAV TUX on 2006-10-07
> **aysiu said:**
> Do you want to post your Knoppix hack, in case someone else might find it useful?

By the way, I've changed a few things.

There's now a removal script as well, and both scripts (installation and removal) have little narrations to let you know what the script is trying to do.

I'll try out your new script first it may work as is.

---

### Post by RAV TUX on 2006-10-07
> **maniacmusician said:**
> oh i see. It's actually really cpu intensive for me, so i dont think i'm going to stick with it at the moment. didnt know it was based on firefox, that explains the ram consumption lol. it's interesting, i'll be keeping an eye on it.

Think of Songbird not just as a media player but a browser also, since it is a hybrid.

---

### Post by maniacmusician on 2006-10-07
true, but it doesnt really fit into my workflow as a browser. i usually have at least two windows open, with up to 12 tabs in either window.

---

### Post by GStubbs43 on 2006-10-08
> **maniacmusician said:**
> true, but it doesnt really fit into my workflow as a browser. i usually have at least two windows open, with up to 12 tabs in either window.

I actually think they are going to add tabs for better "web browsing!" :KS

---

### Post by RAV TUX on 2006-10-08
> **GStubbs43 said:**
> I actually think they are going to add tabs for better "web browsing!" :KS

It's my understanding, that eventually you will be able to use all Firefox extensions?

---

### Post by GStubbs43 on 2006-10-08
> **yozef said:**
> It's my understanding, that eventually you will be able to use all Firefox extensions?


I was thinking something like, it will allow to use some (most) Firefox extensions from sites such as addons.mozilla.org but it will also have custom extensions, such as iPod compatibility.  [http://www.songbirdnest.com/extensions](http://www.songbirdnest.com/extensions)

---

### Post by GStubbs43 on 2006-10-08
I just set up a blog and added a quick review of Songbird, that I need to do some editing on, but if anyone wants to, you can read it, and comment on it! [Link]("http://gstubbs43.wordpress.com/2006/10/08/songbird-02/trackback/")

---

### Post by etank on 2006-10-08
Will this run on Edgy since it is using the Bon Echo beta of firefox.


Nevermind. I just tried it and it works great. Thanks for the script.

---

### Post by GStubbs43 on 2006-10-08
It should run on Edgy as well, try it out and tell us if it works!
 (I feel like I'm taking over aysiu's thread! haha)

---

### Post by etank on 2006-10-08
I tested. It works great.

---

### Post by Joey French on 2006-10-08
Tested on Edgy, fresh install. Works!

Joey

---

### Post by GStubbs43 on 2006-10-08
[QUOTE=etank]I tested. It works great.[/QUOTE]

[QUOTE=Joey French]Tested on Edgy, fresh install. Works![/QUOTE]

That's great guys, I added it to my review that it works in Edgy as well! :-D :p

---

### Post by damu on 2006-10-09
Thanks Aysiu  for this script. I am always dual booting from Windows (Flash MX, Director, and a few others...) to Ubuntu (for everything else), I now have the same great player in both platforms. And what a nice player! :) 

local and online media seems to merge in one stream with Songbird in such a fluent and obvious way...

---

### Post by RAV TUX on 2006-10-09
> **aysiu said:**
> Do you want to post your Knoppix hack, in case someone else might find it useful?

By the way, I've changed a few things.

There's now a removal script as well, and both scripts (installation and removal) have little narrations to let you know what the script is trying to do.


> **yozef said:**
> I'll try out your new script first it may work as is.

New script works in Knoppix(Debian) fine as is

---

### Post by angkor on 2006-10-09
Tested the script on dapper, works perfectly.

Can't seem to find an option to display cover art yet.

---

### Post by orev on 2006-10-09
Thanks for the script!

Works here.  (Ubuntu Dapper)

---

### Post by GStubbs43 on 2006-10-11
Just want to say a few things:

1) This script also works in enlightenment (tried with the ELive Live CD with both E16 and E17)

2) 0.2 final release will be coming out soon, so you may need to update your script sometime soon. ;)

3) When did you become a mod again aysiu? Or have you been a mod for a long time and I just don't remember? I know random, but...

---

### Post by aysiu on 2006-10-11
It's going to jump from 0.2 to 2.0? That's quite a leap! Well, I'll keep a lookout for version changes.

I just became a moderator again today, yes.

---

### Post by GStubbs43 on 2006-10-11
woops.. I meant 0.2 Final (vs 0.2 RC2)! haha

Have fun as a moderator again!

P.S. I remember my last suggestion (if you want to) you should now move this to the Howto as "Howto: Install Songbird) or something like that. I think it would get more attention there. ;)

---

### Post by ericesque on 2006-10-12
Hey, thanks for the script Aysiu (can you write that phonetically for me?) I've been wondering if Songbird was vaporware for a while now.  It seems they've put together quite an app.  I think I'm going to stick with Listen for now, but it'll be nice to play around with sb from time to time.

---

### Post by GStubbs43 on 2006-10-12
> **ericesque said:**
> Hey, thanks for the script Aysiu (can you write that phonetically for me?)

I'm obviously not aysiu, but this is what I'm pretty sure it is, even though sometimes I just say A-Sue, I think he has it as A Y Siu, as his initials and last name. I *think* ;)

---

### Post by mozetti on 2006-10-12
FYI -- I've let the rest of the fledglings over at Songbird know about this thread.

[http://www.songbirdnest.com/node/830](http://www.songbirdnest.com/node/830)

---

### Post by GStubbs43 on 2006-10-12
> **aysiu said:**
> Is it possible for a script to exist that gives that option? Yes. Do I know enough about writing scripts to present that option? No.


Hey, I think I got it (I basically took it right out of your upgrade script) :mrgreen: 

```


echo -e -n "

Do you still wish to remove personal Songbird settings [y/n]? "
while true
do
  read ans
  case $ans in
       Y|y) break ;;
  [Yy][Ee][Ss]) break ;;
       N|n) exit ;;
  [Nn][Oo]) exit ;;
         *) echo -n "Invalid command. Please answer yes or no [y/n] " ;;
  esac
done

sudo rm -r ~/.songbird

```


Just add that to the end of the script. 8)

---

### Post by aysiu on 2006-10-12
I think I will. I'll post back when the script is updated.

---

### Post by GStubbs43 on 2006-10-12
By the way, I *did* test it and it works

Oh, and was I right on your name? ;)

---

### Post by aysiu on 2006-10-12
Great. I'll add it in later today.

You were right about my name.

---

### Post by rocknrolf77 on 2006-10-12
Fired songbird up and it just shut's down. Can't understand the problem.

```
rolf@rolf-desktop:~$ Songbird
*** UPLOADING METRICS ***sbWindowCloak: cloaking..
terminate called after throwing an instance of 'std::bad_alloc'
  what():  St9bad_alloc
Avbrutt (SIGABRT)
rolf@rolf-desktop:~$


```

---

### Post by GStubbs43 on 2006-10-12
rock, have you tried removing it, along with ~/.songbird , and then reinstalling it?

---

### Post by rocknrolf77 on 2006-10-12
No, i'll ry that

---

### Post by rocknrolf77 on 2006-10-12
Didn't help anything. It just quits on me like before. I don't understand the output from the terminal. Hope someone else here who do comes along. Really wan't to try out this songbird. Have just tried the old one. :)

---

### Post by Anonii on 2006-10-12
Is it worth trying Songbird now, or should I wait till final 0.2?

This question is easily translated to "How stable is Songbird, right now? Is it as good as the screenshots show?".

---

### Post by GStubbs43 on 2006-10-12
> **rocknrolf77 said:**
> Didn't help anything. It just quits on me like before. I don't understand the output from the terminal. Hope someone else here who do comes along. Really wan't to try out this songbird. Have just tried the old one. :)

hmm... I'm not sure then, hopefully someone can help you, it's a great program!

[QUOTE=Anonii]Is it worth trying Songbird now, or should I wait till final 0.2?

This question is easily translated to "How stable is Songbird, right now? Is it as good as the screenshots show?".[/QUOTE]

I think it is very stable (you can see my {not-so-good} review on my blog... I've never seen any major problems with it besides rocknrolf77's... Which I don't get why he has that problem... :-k But yeah, try it, it will automatically update itself when the final releade comes out anyway (I think)

---

### Post by ~LoKe on 2006-10-12
It runs fine for me, it seems, but it seems incredibly resource intensive.  Gets a big thumbsdown for me until it runs smoother.

---

### Post by Anonii on 2006-10-12
Well, I'll try it out. Submitting some bug reports and helping, wont hurt.

---

### Post by aysiu on 2006-10-12
I've updated the removal script to ask if you want the preferences folder removed or not.

---

### Post by GStubbs43 on 2006-10-13
Yay! I really don't know *why*... but for some reason I wanted that in it. ;)

---

### Post by aysiu on 2006-10-13
It's not a shame to want that. Thanks for suggesting that.

By the way, I've updated the script to install RC3.

Haven't tested it yet, though.

---

### Post by _lynX on 2006-10-14
> **aysiu said:**
> It's not a shame to want that. Thanks for suggesting that.

By the way, I've updated the script to install RC3.

Haven't tested it yet, though.

It doesn't appear to like the fact that I'm trying to install over my RC2 installation. Using the uninstall script from your site and then using the install script again worked fine.

---

### Post by aysiu on 2006-10-14
> **_lynX said:**
> It doesn't appear to like the fact that I'm trying to install over my RC2 installation.
If I'm not mistaken, you shouldn't have to reinstall over RC2. I think you can update to RC3 through the Songbird interface. I can modify the script to overwrite a previous Songbird installation, though.

---

### Post by _lynX on 2006-10-14
> **aysiu said:**
> If I'm not mistaken, you shouldn't have to reinstall over RC2. I think you can update to RC3 through the Songbird interface. I can modify the script to overwrite a previous Songbird installation, though.

You're right. I did not realize that.

---

### Post by GStubbs43 on 2006-10-14
I have *another* icon suggestion. ;)

This is the default for Windows and Mac (I think) and is automatically downloaded with Songbird, so you won't have to have people download one from your site. It gets downloaded to /usr/local/bin/songbird/chrome/icons/default/default.xpm so, your script could asically be this:

```
#/bin/bash
if [ -d /usr/local/bin/songbird ]; then
  echo "
You appear to already have Songbird installed. You should use the self-update function in Songbird instead of using this script.
"
exit
fi
echo "
Downloading Songbird from the internet--this could take several minutes, even on a broadband connection. Please be patient.
"
wget -c http://download.songbirdnest.com/installer/linux/i686/Songbird_0_2_RC3_linux-i686.tar.gz
echo "
Unzipping the .tar.gz we downloaded.
"
tar -xvzf Songbird_0_2_RC3_linux-i686.tar.gz
echo "
Moving Songbird to its own folder.
"
sudo mv Songbird /usr/local/bin/songbird
echo "
Removing the original .tar.gz
"
rm Songbird_0_2_RC3_linux-i686.tar.gz
echo "
Making an executable for Songbird.
"
sudo ln -s /usr/local/bin/songbird/Songbird /usr/bin/Songbird
echo "
Putting the Songbird icon in the correct folder.
"
sudo cp /usr/local/bin/songbird/chrome/icons/default/default.xpm /usr/share/pixmaps/songbird.png
echo "
Downloading the menu entry for Songbird.
"
wget -c http://www.psychocats.net/ubuntu/songbird.desktop
echo "
Moving the menu entry to the correct folder.
"
sudo mv songbird.desktop /usr/share/applications/songbird.desktop
echo "
After you refresh your menus, Songbird should be available as an application within the menus. If not, the launcher for Songbird should use the command Songbird (with a capital S).
"

```

It removes the part with downloading an icon from psychocats.net. Sorry if this was kind of confusing...

---

### Post by user1397 on 2006-10-15
hey aysiu, how come your script starts out with **#/bin/bash** instead of  **#!/bin/bash** ???  i was just having a discussion on this matter here: [http://ubuntuforums.org/showthread.php?t=276891](http://ubuntuforums.org/showthread.php?t=276891)

---

### Post by aysiu on 2006-10-15
I forgot the exclamation point? I'll put it in.

GStubbs43, I've put the official icon on Psychocats. As far as I can tell, it's not in the .tarball from the Songbird website, though.

**Edit**: Sorry, you're right. It is there, but as an XPM. So I uploaded to Psychocats the .png you have attached to your post.

---

### Post by user1397 on 2006-10-15
> **aysiu said:**
> I forgot the exclamation point? I'll put it in.how was it working for people though?  it is mind boggling that it worked without the shebang.  btw, your script inspired me to write my first useful script ever, for tovid: [http://ubuntuforums.org/showthread.php?t=183936](http://ubuntuforums.org/showthread.php?t=183936)

so thanks!  (i basically copied/pasted some of the commands and "echos" from your script to mine!!:p)

---

### Post by aysiu on 2006-10-15
Awesome. Most of my script stuff I've just copied off other people's scripts, too!

I don't know why the script was working without the shebang, but it was.

By the way, does anyone know why a lowercase symlinked /usr/bin/songbird won't work, but an uppercase (/usr/bin/Songbird) one will?

---

### Post by kopilo on 2006-10-15
> **aysiu said:**
> I wrote [a script that installs Songbird for you](http://ubuntuforums.org/showthread.php?t=273162). I just updated it to install RC3.

If you already have RC2 installed, Songbird has an update manager that will upgrade to RC3.
I know I am being a bit picky but you should mention which version of EDIT [strike]Ubuntu[/strike] Linux your script is for.. There is a i686 and a 64 bit version of Songbird.

Same to this How To.

---

### Post by aysiu on 2006-10-15
It's x86, not AMD64.

---

### Post by kopilo on 2006-10-15
> **aysiu said:**
> It's x86, not AMD64.
Same difference. x86_64.

---

### Post by aysiu on 2006-10-15
i686, not x86_64.
Does that clarify it better for you?

I was using the Ubuntu terminology (see attached screenshot).

---

### Post by kopilo on 2006-10-15
ahh ok, thanks.

---

### Post by aysiu on 2006-10-15
Can you do me a favor?

I don't have AMD64 Ubuntu, so I don't know what the output of this command looks like for you.

Could you post back the output of ```
uname -m
```?

---

### Post by kopilo on 2006-10-15
Sure thing
```
kopilo@kopilo-desktop:~$ uname -m
x86_64
kopilo@kopilo-desktop:~$
```
Ohh wait you did say which version your script was for... Sorry.

---

### Post by aysiu on 2006-10-15
Thanks. I'm trying to work in some kind of if/then thing into the script to autodetect what architecture you have and install the appropriate Songbird version.

---

### Post by kopilo on 2006-10-15
Cool, that would be awesome and could be applied to many different programs, such as Firefox, Sunbird (if it ever goes 64), xmms(2) etc.

---

### Post by aysiu on 2006-10-15
> **kopilo said:**
> Cool, that would be awesome and could be applied to many different programs, such as Firefox, Sunbird (if it ever goes 64), xmms(2) etc.
Would you mind helping me test the modified version?

I've tested it for x86 (or i686), but I don't have an x86_64 (AMD64) computer, so I can't test that bit.

Paste this code into a text editor and save it as *installsongbird.sh* on your desktop: ```
#!/bin/bash
if [ -d /usr/local/bin/songbird ]; then
  echo "
You appear to already have Songbird installed. To get the newest version, you should use the self-update function in Songbird instead of using this script.
"
exit
fi
cd
uname -m > tmp.arch.txt
if grep -q "64" tmp.arch.txt ; then
echo "
You appear to have an AMD64 architecture. Do you want to install the 64-bit version of Songbird? [y/n]
"
while true
do
  read ans
  case $ans in
       Y|y) echo "Downloading Songbird from the internet--this could take several minutes, even on a broadband connection. Please be patient." ; wget -c http://download.songbirdnest.com/installer/linux/x86_64/Songbird_0_2_RC3_linux-x86_64.tar.gz ; echo "Unzipping the .tar.gz we downloaded." ; tar -xvzf Songbird_0_2_RC3_linux-x86_64.tar.gz ; break ;;
  [Yy][Ee][Ss]) echo "Downloading Songbird from the internet--this could take several minutes, even on a broadband connection. Please be patient." ; wget -c http://download.songbirdnest.com/installer/linux/x86_64/Songbird_0_2_RC3_linux-x86_64.tar.gz ; echo "Unzipping the .tar.gz we downloaded." ; tar -xvzf Songbird_0_2_RC3_linux-x86_64.tar.gz ; break ;;
       N|n) echo "We have not properly detected your architecture. Songbird installation script quitting." ; exit ;;
  [Nn][Oo]) echo "We have not properly detected your architecture. Songbird installation script quitting." ; exit ;;
         *) echo -n "Invalid command. Please answer yes or no [y/n] " ;;
  esac
done
elif grep -q "86" tmp.arch.txt ; then
echo "
You appear to have an x86 architecture. Do you want to install the i686 version of Songbird? [y/n]
"
while true
do
  read ans
  case $ans in
       Y|y) echo "Downloading Songbird from the internet--this could take several minutes, even on a broadband connection. Please be patient." ; wget -c http://download.songbirdnest.com/installer/linux/i686/Songbird_0_2_RC3_linux-i686.tar.gz ; echo "Unzipping the .tar.gz we downloaded." ; tar -xvzf Songbird_0_2_RC3_linux-i686.tar.gz ; break ;;
  [Yy][Ee][Ss]) echo "Downloading Songbird from the internet--this could take several minutes, even on a broadband connection. Please be patient." ; wget -c http://download.songbirdnest.com/installer/linux/i686/Songbird_0_2_RC3_linux-i686.tar.gz ; echo "Unzipping the .tar.gz we downloaded." ; tar -xvzf Songbird_0_2_RC3_linux-i686.tar.gz ; break ;;
       N|n) echo "We have not properly detected your architecture. Songbird installation script quitting." ; exit ;;
  [Nn][Oo]) echo "We have not properly detected your architecture. Songbird installation script quitting." ; exit ;;
         *) echo -n "Invalid command. Please answer yes or no [y/n] " ;;
  esac
done
else
  echo "This script works for only x86 and AMD64 architectures."
  exit 1
fi
rm tmp.arch.txt
echo "

Moving Songbird to its own folder.

"
sudo mv Songbird /usr/local/bin/songbird
echo "

Removing the original .tar.gz

"
rm Songbird_0_2_RC3_linux-i686.tar.gz
echo "

Making an executable for Songbird.

"
sudo ln -s /usr/local/bin/songbird/Songbird /usr/bin/Songbird
echo "

Downloading an icon for Songbird.

"
wget -c http://www.psychocats.net/ubuntu/songbirdicon.png
echo "

Putting the Songbird icon in the correct folder.

"
sudo mv songbirdicon.png /usr/share/pixmaps/songbird.png
echo "

Downloading the menu entry for Songbird.

"
wget -c http://www.psychocats.net/ubuntu/songbird.desktop
echo "

Moving the menu entry to the correct folder.

"
sudo mv songbird.desktop /usr/share/applications/songbird.desktop
echo "

After you refresh your menus, Songbird should be available as an application within the menus. If not, the launcher for Songbird should use the command Songbird (with a capital S).

"
``` Then to run it: ```
cd ~/Desktop
sh installsongbird.sh
``` First try saying "no" when it asks if you're using AMD64. Make sure it quits when you say "no." Then run it again and say "yes." If it doesn't work, please post the entire script's output back here. Thanks.

---

### Post by kopilo on 2006-10-15
Sure thing, just have to uninstall it first. ;)

---

### Post by aysiu on 2006-10-15
Thanks for this. I know uninstalling and testing an installation can be a pain.

It's for the greater good, of course, but thanks, nonetheless.

---

### Post by kopilo on 2006-10-15
Ok here is the output of the script
```
You appear to have an AMD64 architecture. Do you want to install the
64-bit version of Songbird? [y/n]

y
Downloading Songbird from the internet--this could
take several minutes, even on a broadband connection. Please be
patient.
wget: missing URL
Usage: wget [OPTION]... [URL]...

Try `wget --help' for more options.
installsongbird.sh: line 24: http://download.songbirdnest.com/installer/linux/x86_64/Songbird_0_2_RC3_linux-x86_64.tar.gz: No such file or directory
Unzipping the .tar.gz we downloaded.
tar: option requires an argument -- f
Try `tar --help' or `tar --usage' for more information.
installsongbird.sh: line 26: Songbird_0_2_RC3_linux-x86_64.tar.gz: command not found


Moving Songbird to its own folder.


mv: cannot stat `Songbird': No such file or directory


Removing the original .tar.gz


rm: cannot remove `Songbird_0_2_RC3_linux-i686.tar.gz': No such file or directory


Making an executable for Songbird.




Downloading an icon for Songbird.


--17:56:24--  http://www.psychocats.net/ubuntu/songbirdicon.png
           => `songbirdicon.png'
Resolving www.psychocats.net... 64.14.68.87
Connecting to www.psychocats.net|64.14.68.87|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 12,543 (12K) [image/png]

100%[=================================================================================================================>] 12,543        18.64K/s

17:56:27 (18.61 KB/s) - `songbirdicon.png' saved [12543/12543]



Putting the Songbird icon in the correct folder.




Downloading the menu entry for Songbird.


--17:56:27--  http://www.psychocats.net/ubuntu/songbird.desktop
           => `songbird.desktop'
Resolving www.psychocats.net... 64.14.68.87
Connecting to www.psychocats.net|64.14.68.87|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 7,467 (7.3K) [text/plain]

100%[=================================================================================================================>] 7,467         19.53K/s

17:56:29 (19.48 KB/s) - `songbird.desktop' saved [7467/7467]



Moving the menu entry to the correct folder.




After you refresh your menus, Songbird should be available as an
application within the menus. If not, the launcher for Songbird should
use the command Songbird (with a capital S).

```
So you can give yourself a pat on the back.
Although when I copied and pasted I had to ensure all ';'
were on the right line.

Basically some lines started like
 ; echo
so I made it
;
echo

However when "Sunbird" is run from menu I get this error.
> Details: Failed to execute child process "Songbird" (No such file or directory)

And when run in terminal
> Songbird
bash: Songbird: command not found

I gather it didn't install, due to url error, but at least everything else seemed to have worked.

---

### Post by aysiu on 2006-10-15
No, no pat on the back yet.

Go ahead and delete that one.

Could you do me a favor and run [this removal script?](http://www.psychocats.net/ubuntu/removesongbird.sh)

And then run [this installation script?](http://www.psychocats.net/ubuntu/installsongbird.sh)

I have a feeling that somehow the copy and paste might have messed up the line breaks on part of the script.

---

### Post by kopilo on 2006-10-15
Ok I stoped the script and ran the removal script...

here is the output.
```
 bash removesongbird.sh

Removing Songbird folder.

Password:

Removing launcher.


Removing entry for Songbird.


Removing Songbird icon.


Do you want to keep your Songbird personal preferences even though the applicati on is removed? [y/n]

n
Removing your Songbird preferencesrm: remove write-protected regular file `/home /kopilo/.songbird/3o0lkpu5.default/extensions/{1EBE0262-05BE-46e3-ACF3-44F6A3909 39C}/chrome/content/wikipedia.js'?
rm: remove write-protected regular file `/home/kopilo/.songbird/3o0lkpu5.default/extensions/{1EBE0262-05BE-46e3-ACF3-44F6A390939C}/chrome/content/extension.js'? y
rm: remove write-protected regular file `/home/kopilo/.songbird/3o0lkpu5.default/extensions/{1EBE0262-05BE-46e3-ACF3-44F6A390939C}/chrome/content/extension.xul'? yes
rm: remove write-protected regular file `/home/kopilo/.songbird/3o0lkpu5.default/extensions/{1EBE0262-05BE-46e3-ACF3-44F6A390939C}/chrome/content/wikipedia.xul'? ...
rm: remove write-protected regular file `/home/kopilo/.songbird/3o0lkpu5.default/extensions/{1EBE0262-05BE-46e3-ACF3-44F6A390939C}/install.rdf'? ....
rm: remove write-protected regular file `/home/kopilo/.songbird/3o0lkpu5.default/extensions/{1EBE0262-05BE-46e3-ACF3-44F6A390939C}/chrome.manifest'? ...

Songbird is now removed from your system.

```

---

### Post by kopilo on 2006-10-15
Ok I ran the install script, songbird installed fine. (buffer wasn't big enough to capture all the output)

The menu item also works.

Now you deserve a big pat on the back. :)

---

### Post by aysiu on 2006-10-15
That's weird. Your Songbird preference folder has write-protected files in it? Weird.

In any case, that's fine. You can keep the preferences is in there.

What happens when you run the installation script afterwards?

**Edit**: Oh, guess it worked! Thanks for helping me test that.

---

### Post by kopilo on 2006-10-15
> **aysiu said:**
> That's weird. Your Songbird preference folder has write-protected files in it? Weird.

In any case, that's fine. You can keep the preferences is in there.

What happens when you run the installation script afterwards?

**Edit**: Oh, guess it worked! Thanks for helping me test that.
You're welcome, thank you for letting me help you.

[COLOR="Sienna"][CENTER]Ubuntu - "I am what I am because of who we all are".[/COLOR][/CENTER]

---

### Post by user1397 on 2006-10-15
has the menu entry ever worked for anybody automatically?   cause on my tovid script, it didn't work for me.

---

### Post by Polygon on 2006-10-15
The script worked perfectly for me (running a k7 kernel, or i686, added a menu entry for me to answer your question erik

thanks. Once again aysiu strikes again!

btw songbird rocks.

---

### Post by aysiu on 2006-10-16
> **Polygon said:**
> The script worked perfectly for me (running a k7 kernel, or i686, added a menu entry for me to answer your question erik

thanks. Once again aysiu strikes again!

btw songbird rocks.
Glad to know even the modified script is still working. Thanks, Polygon.

Erik1397, I've responded to you [in your Tovid thread](http://ubuntuforums.org/showthread.php?p=1622309#post1622309) about your .desktop file.

---

### Post by Brynster on 2006-10-16
Big shout out of thanks to you Aysiu + others involved in testing and fixing the script.

Did a full fresh Edgy install yesterday ran automatix ands then Songbird script all work flawlessly. You have just made onto my mandatory must have installs for all new Ubuntu installs..


Many Many thanks.

---

### Post by aysiu on 2006-10-16
Thanks for the feedback, Brynster. It's good to know it's working out for you.

---

### Post by GStubbs43 on 2006-10-18
Hey, FYI... [http://www.getdeb.net/](http://www.getdeb.net/) now has a Songbird 0.2 RC3 deb package! I haven't tried it though...

EDIT: Tried it, it was a very slow download, it didn't create a menu icon and it didn't even put a link into /usr/bin. For now, I would stick with this script vs the deb. :)

---

### Post by GStubbs43 on 2006-10-19
Update!

x86-64
[http://download.songbirdnest.com/installer/linux/x86_64/Songbird_0_2_linux-x86_64.tar.gz](http://download.songbirdnest.com/installer/linux/x86_64/Songbird_0_2_linux-x86_64.tar.gz)

i686
[http://download.songbirdnest.com/installer/linux/i686/Songbird_0_2_linux-i686.tar.gz](http://download.songbirdnest.com/installer/linux/i686/Songbird_0_2_linux-i686.tar.gz)

---

### Post by aysiu on 2006-10-19
> **GStubbs43 said:**
> Update!

x86-64
[http://download.songbirdnest.com/installer/linux/x86_64/Songbird_0_2_linux-x86_64.tar.gz](http://download.songbirdnest.com/installer/linux/x86_64/Songbird_0_2_linux-x86_64.tar.gz)

i686
[http://download.songbirdnest.com/installer/linux/i686/Songbird_0_2_linux-i686.tar.gz](http://download.songbirdnest.com/installer/linux/i686/Songbird_0_2_linux-i686.tar.gz)
I've updated the script accordingly.

Anyone want to test it?

---

### Post by GStubbs43 on 2006-10-19
I just downloaded the script and it says RC3 in the wget's and tar's... But for anyone who already has Songbird, you should remove it and reinstall the new one. There are buugs in RC3 that won't be fixed just by upgrading. ;)

---

### Post by aysiu on 2006-10-19
> **GStubbs43 said:**
> I just downloaded the script and it says RC3 in the wget's and tar's... But for anyone who already has Songbird, you should remove it and reinstall the new one. There are buugs in RC3 that won't be fixed just by upgrading. ;)
Clear your browser cache and try again.

---

### Post by GStubbs43 on 2006-10-19
Got it! :) Did you just "search and replace" RC3_ ? 

If you did... I tried it (I did that before I got the new script) and it works perfectly. If not... then I'm not sure if it works or not.

---

### Post by aysiu on 2006-10-19
> **GStubbs43 said:**
> Got it! :) Did you just "search and replace" RC3_ ? 

If you did... I tried it (I did that before I got the new script) and it works perfectly. If not... then I'm not sure if it works or not.
I didn't do a find/replace. I looked to find the actual name of the URL and replaced the old one with that and replaced the name of the .tar.gz with the actual new name.

---

### Post by GStubbs43 on 2006-10-19
Well, that does the same thing... So yeah, it works on my computer... i686 version.

---

### Post by kopilo on 2006-10-19
> **aysiu said:**
> I've updated the script accordingly.

Anyone want to test it?

Testing now.
[INDENT][COLOR="Navy"]sudo bash installsongbird.sh[/COLOR][/INDENT]
EDIT: Seemed to have worked, not sure how to test which version song bird is... 

*Note Songbird did automatically update itself before I ran the script so I uninstalled and ran the new script. Doesn't seem to be auto updating so I take it, that it is the latest version*

---

### Post by aysiu on 2006-10-19
There is no version 3.

Right now, it's version 0.2. That's the latest version.

Before that, it was 0.2 RC3, which means "release candidate 3," an earlier version than 0.2, which is the final release.

---

### Post by kopilo on 2006-10-19
umm, yeah I looked at the "about screen" has version "20061018" I gather that is year, month and day ;)

---

### Post by aysiu on 2006-10-20
> **kopilo said:**
> umm, yeah I looked at the "about screen" has version "20061018" I gather that is year, month and day ;)
When you look at the Download screen, all the versions there are 0.2.

The ones available via this script are the ones circled in green.

---

### Post by kopilo on 2006-10-20
Yeah, indeed, sorry I'm use to Firefox/Deer Park, their versioning system seems to be slightly more explicit then Songbird.

---

### Post by hanzomon4 on 2006-10-21
Nice script, mine doing a little beginners tutorial on shell scripting?

---

### Post by user1397 on 2006-10-21
> **hanzomon4 said:**
> Nice script, mine doing a little beginners tutorial on shell scripting?actually, no tutorial is really needed.  all you have to do is download his script, look at it, and try things out by yourself by pasting some of the commands from your script to yours.  that's exactly how i made this script: [http://ubuntuforums.org/showthread.php?t=183936](http://ubuntuforums.org/showthread.php?t=183936)

---

### Post by weird_c00kie on 2006-10-23
> **aysiu said:**
> I just created an installation script for Songbird 0.2, in case anyone's interested.

The instructions and script can be found here:
[http://www.psychocats.net/ubuntu/songbird](http://www.psychocats.net/ubuntu/songbird)

The script is for x86, not AMD64.

awesome man, thanks :D

i don't know if anyone's mentioned it already, but your script and the installation worked perfectly fine on my amd64 :D

and i can finally import my itunes library!!!!  i am this much step closer to never needing XP again :D

---

### Post by gosh on 2006-10-23
thnx for this script. 
worked as a charm!

---

### Post by Vexed Arcanist on 2006-11-03
Anyone know what the system overhead is currently for Songbird on Ubuntu?  I know on Windows XP it was enormously high, 55mb and cpu usage ~30% (older machine).  Compare that to the 7mb for WMP and ~14mb for WinAmp.  I stopped using it when I saw those numbers, on Windows.

How does Songbird stack up against Amarok or Banshee or Listen Player or <insert favorite audio player>?

Yes, I am aware Songbird is relatively Alpha, but this is the most crucial fix required, IMO.  Get that overhead down.

---

### Post by user1397 on 2006-11-08
hey aysiu, i see that in your songbird.desktop file, you have the gnome entry for songbird (the exact line reads:
Categories=GNOME;GTK;Application;AudioVideo;X-Ximian-Main;X-Red-Hat-Base; )

how would you write the kde version of that line?

---

### Post by aysiu on 2006-11-08
> **erik1397 said:**
> hey aysiu, i see that in your songbird.desktop file, you have the gnome entry for songbird (the exact line reads:
Categories=GNOME;GTK;Application;AudioVideo;X-Ximian-Main;X-Red-Hat-Base; )

how would you write the kde version of that line?
I don't know. To be honest, I just took the rhythmbox.desktop file and did a find/replace of *rhythmbox* for *songbird*.

---

### Post by mhancoc7 on 2006-11-08
This is awesome!! I really like the script and it works great in Ubuntu CE.
Thanks, Jereme

---

### Post by user1397 on 2006-11-08
> **aysiu said:**
> I don't know. To be honest, I just took the rhythmbox.desktop file and did a find/replace of *rhythmbox* for *songbird*.ah, well that just gaave me an idea. i'll go to some .desktop file and see the way it is written (in kde of course)

maybe then you should add the kde version of that, so that kubuntu users can enjoy the same .desktop file.

---

### Post by user1397 on 2006-11-10
arite looking at the amarok .desktop file, in kubuntu edgy, the last line reads: 
Categories=Qt;KDE;AudioVideo;Player;

i dont know how it works tho;  do you have to put the gnome and kde categories in 2 separate lines?  or do you just make it all on one line?

for example, either:

Categories=Gnome;GTK;Application;AudioVideo;
Categories=Qt;KDE;AudioVideo;Player;

OR:
Categories=Gnome;GTK;Application;AudioVideo;Qt;KDE;AudioVideo;Player;

whatdaya think?

---

### Post by knucklehead2354 on 2006-11-10
Worked like a charm on my computer.  Thanks! :)

---

### Post by Patrick K. on 2006-11-11
Installation was a success! Everything working as it should be. Songbird has gathered my music folder and now playing it's contents.

06-Indidginus  Dusty Lands-Magnatune Compilation-1.mp3

And I hear it too! :P

---

### Post by xmastree on 2006-11-11
Nope. not for me...

[ATTACH]19162[/ATTACH]

Although I think I know the problem. Clicking the 'more' button took me to [this page](http://publicsvn.songbirdnest.com/trac/wiki/CoreWrapperFailure) which links to [this one](http://publicsvn.songbirdnest.com/trac/wiki/SettingUpGStreamer)

So, it needs gstreamer 0.10 but this (Breezy) installation is using 0.8 :-k 

My laptop is running Dapper, but I don't have any music on its humble 4GB drive. However, I've just bought a 40GB for it, and I've just downloaded the 6.10 CD... Let's see what happens. [-o<

---

### Post by WalmartSniperLX on 2006-11-11
Installed perfectly :D Thanks a lot ;)

---

### Post by xmastree on 2006-11-11
> **xmastree said:**
> Let's see what happens. [-o<
Well, the script worked, Songbird opens, but I have to say...

This is the worst pile of crash-happy junk I have ever seen!

It's bloody awful, in every way. When I did manage to get it to play something without crashing, there was still no sound at all.

**[SIZE="4"]Absolute rubbish![/SIZE]**

---

### Post by GStubbs43 on 2006-11-11
Anyway.... ;)

I think I know how to make it /usr/bin/songbird instead of Songbird. It's messier, but it works. :)

create a file in /usr/bin named songbird and add ```
#!/bin/sh
/usr/local/bin/Sonbird/Songbird
```
then do ```
sudo chmod +x /usr/bin/songbird
``` then ```
sudo chmod 777 /usr/bin/songbird
```

For the orginal file you can add it to your website and wget it, then ```
sudo mv songbird /usr/bin/
```

---

### Post by John.Michael.Kane on 2006-11-11
aysiu great script. SB installed without issue on an amd64 system.

---

### Post by aysiu on 2006-11-11
> **SD-Plissken said:**
> aysiu great script. SB installed without issue on an amd64 system.
Good to hear, especially since I don't have an AMD64 computer, so I can't test it for that.

---

### Post by mrphd on 2006-11-14
Great script. I modified it to get the latest nightly they have (2006.11.10) by changing a couple of lines in the script and it works great. Songbird is looking like a very promising program...

---

### Post by aysiu on 2006-11-14
> **mrphd said:**
> Great script. I modified it to get the latest nightly they have (2006.11.10) by changing a couple of lines in the script and it works great. Songbird is looking like a very promising program...
Mind posting the modification, in case others would also like to get the latest nightly?

---

### Post by mrphd on 2006-11-14
No problem. To use this, just download the attached file to your desktop and rename by opening a terminal and entering:

cd ~/Desktop
mv installsongbird.txt installsongbird.sh

then proceed as in step 2 at [http://www.psychocats.net/ubuntu/songbird](http://www.psychocats.net/ubuntu/songbird). Let me know if there are any problems.

If you already have a version of Songbird installed, you should use the remove script and instructions also at [http://www.psychocats.net/ubuntu/songbird](http://www.psychocats.net/ubuntu/songbird)

---

### Post by JurB on 2006-11-14
> **xmastree said:**
> Well, the script worked, Songbird opens, but I have to say...

This is the worst pile of crash-happy junk I have ever seen!

It's bloody awful, in every way. When I did manage to get it to play something without crashing, there was still no sound at all.

**[SIZE="4"]Absolute rubbish![/SIZE]**

Amen!

---

### Post by kopilo on 2006-11-14
Just in case people are looking for the directory of Songbird because they want to install feathers or want not, the one released by aysiu installs songbird to > /usr/local/bin/songbird

---

### Post by GStubbs43 on 2006-11-15
New nightly, here's a script for it. Follow MrPhD's instructions.
[Here]("http://bugzilla.songbirdnest.com/buglist.cgi?query_format=advanced&short_desc_type=allwordssubstr&short_desc=&product=Songbird&target_milestone=0.2.1&long_desc_type=substring&long_desc=&bug_file_loc_type=allwordssubstr&bug_file_loc=&status_whiteboard_type=allwordssubstr&status_whiteboard=&bug_status=RESOLVED&emailtype1=substring&email1=&emailassigned_to2=1&emailreporter2=1&emailqa_contact2=1&emailcc2=1&emailtype2=substring&email2=&bugidtype=include&bug_id=&votes=&chfieldfrom=&chfieldto=Now&chfieldvalue=&cmdtype=doit&order=Reuse+same+sort+as+last+time&query_based_on=Fixed+0.2.1&field0-0-0=noop&type0-0-0=noop&value0-0-0=") are the fixed bugs since 0.2.

EDIT: If anyone used this script and it didn't work, it should now. I put the wrong file name in one part of the script.

---

### Post by nrwilk on 2006-11-16
Thanks so much for the handy script, Aysiu.

Songbird installed seemingly perfectly.

I do have a pretty major problem, though.  Songbird will not play any music whatsoever.  It will not play from a URL, from my harddrive, or from streams.  It also reports all tracks as being 0:00 minutes in length.

It repeats these two errors in the console thousands of times:
```
(xulrunner-bin:10371): GStreamer-CRITICAL **: gst_element_get_state: assertion `GST_IS_ELEMENT (element)' failed

(xulrunner-bin:10371): GLib-GObject-CRITICAL **: g_object_get: assertion `G_IS_OBJECT (object)' failed

```

I really like the look of songbird, I think it may even replace Amarok as my music player of choice on Linux.

Thank you for any help! :) 

nrwilk

---

### Post by mrphd on 2006-11-16
nrwilk: I think that you should enter a bug report at [http://bugzilla.songbirdnest.com/](http://bugzilla.songbirdnest.com/). 

Also, make sure you are using the latest nightly build as there have been a long list of fixes since the 0.2 release. Anyway, 0.2.1 should be released soon so you might want to just wait for that and see if you get the same problems.

---

### Post by nrwilk on 2006-11-16
Yes, I didn't remember to mention this, but I get the same behavior in your nightly build as well.  Also, running Songbird as root does not make a difference.

---

### Post by patagonik on 2006-11-16
How is it possible to have so many cool people around? Thanks a lot for the script... 2 minutes and i'm just melting of joy with Songbird... this is great!!! I love ubuntu!!! WHO said there wasn't iTunes in Linux...??? He was damn right!!! We have something way better!!!

Do not misunderstand PRICE and VALUE folks!

the patagonik penguin!

---

### Post by adewale on 2006-11-19
the script didn't work 4me. i don't have an internet connection. i downloaded the file in windows with my gprs phone and copied to linux what can i do plz help

---

### Post by GStubbs43 on 2006-11-19
[QUOTE=patagonik] WHO said there wasn't iTunes in Linux...??? He was damn right!!! We have something way better!!!
[/QUOTE]
Yup, In a lot of ways Songbird is better than iTunes, but remember that Songbird is also available for "them" as well. ("them" as in Windows and OS X users) :cool: 


[QUOTE=adewale]the script didn't work 4me. i don't have an internet connection. i downloaded the file in windows with my gprs phone and copied to linux what can i do plz help[/QUOTE]

Exactly what file did you download? The script, or the files that the script downloads for you, like 
```
http://download.songbirdnest.com/installer/linux/i686/Songbird_0_2_linux-i686.tar.gz
```
```
http://www.psychocats.net/ubuntu/songbirdicon.png
```
```
http://www.psychocats.net/ubuntu/songbird.desktop
```

After you download those three files, put them all on your Desktop (home/username/Desktop) enter these commands in the terminal:
```
cd Desktop/
```
```
tar -xvzf Songbird_0_2_linux-i686.tar.gz
```
```
sudo mv Songbird /usr/local/bin/songbird
```
```
sudo ln -s /usr/local/bin/songbird/Songbird /usr/bin/Songbird
```
```
sudo mv songbirdicon.png /usr/share/pixmaps/songbird.png
```
```
sudo mv songbird.desktop /usr/share/applications/songbird.desktop
```

---

### Post by xmastree on 2006-11-19
> **GStubbs43 said:**
> Yup, In a lot of ways Songbird is better than iTunesExcept for the one major factor that iTunes actually works. :(

*Potentially* better it may be, but right now it's a waste of disk space.

---

### Post by adewale on 2006-11-19
thanks i downloaded both the script and the package but the rest i can't download them now my connection is down but i was able to move the files but when i typed Songbird in terminal i got an error while loading shared libraries: libgtk-x11-2.0.so.0 : cannot open shared object file : No such file or directory  plz what does this mean

---

### Post by n3Cre0 on 2006-11-21
Could it be that Songbird just updated to 0.2.1? Instead of 0.2?

---

### Post by aysiu on 2006-11-21
> **n3Cre0 said:**
> Could it be that Songbird just updated to 0.2.1? Instead of 0.2?
If so, can you post a link?

---

### Post by adewale on 2006-11-21
please someone should please explain the meaning me this libgtk shared library missing

---

### Post by n3Cre0 on 2006-11-21
> **aysiu said:**
> If so, can you post a link?

Seems to be a nightly build :(

Sorry

---

### Post by GStubbs43 on 2006-11-21
> **adewale said:**
> please someone should please explain the meaning me this libgtk shared library missing

I'm not *100% sure,* but you might need to install the ```
libgtk2.0-0
``` package.

---

### Post by forger on 2006-11-30
new version:
[http://download.songbirdnest.com/installer/linux/i686/](http://download.songbirdnest.com/installer/linux/i686/)
[http://download.songbirdnest.com/installer/linux/i686/Songbird_0_2_1_linux_i686.tar.gz](http://download.songbirdnest.com/installer/linux/i686/Songbird_0_2_1_linux_i686.tar.gz)

```

#!/bin/bash
if [ -d /usr/local/bin/songbird ]; then
  echo "
You appear to already have Songbird installed. To get the newest version, you should use the self-update function in Songbird instead of using this script.
"
exit
fi
cd
uname -m > tmp.arch.txt
if grep -q "64" tmp.arch.txt ; then
echo "
You appear to have an AMD64 architecture. Do you want to install the 64-bit version of Songbird? [y/n]
"
while true
do
  read ans
  case $ans in
       Y|y) echo -n "Downloading Songbird from the internet--this could take several minutes, even on a broadband connection. Please be patient." ; wget -c http://download.songbirdnest.com/installer/linux/x86_64/Songbird_0_2_1_linux-x86_64.tar.gz ; echo -n "Unzipping the .tar.gz we downloaded." ; tar -xvzf Songbird_0_2_1_linux-x86_64.tar.gz ; break ;;
  [Yy][Ee][Ss]) echo -n "Downloading Songbird from the internet--this could take several minutes, even on a broadband connection. Please be patient." ; wget -c http://download.songbirdnest.com/installer/linux/x86_64/Songbird_0_2_1_linux-x86_64.tar.gz ; echo -n "Unzipping the .tar.gz we downloaded." ; tar -xvzf Songbird_0_2_1_linux-x86_64.tar.gz ; break ;;
       N|n) echo -n "We have not properly detected your architecture. Songbird installation script quitting." ; exit ;;
  [Nn][Oo]) echo -n "We have not properly detected your architecture. Songbird installation script quitting." ; exit ;;
         *) echo -n "Invalid command. Please answer yes or no [y/n] " ;;
  esac
done
elif grep -q "86" tmp.arch.txt ; then
echo "
You appear to have an x86 architecture. Do you want to install the i686 version of Songbird? [y/n]
"
while true
do
  read ans
  case $ans in
       Y|y) echo -n "Downloading Songbird from the internet--this could take several minutes, even on a broadband connection. Please be patient." ; wget -c http://download.songbirdnest.com/installer/linux/i686/Songbird_0_2_1_linux_i686.tar.gz ; echo -n "Unzipping the .tar.gz we downloaded." ; tar -xvzf Songbird_0_2_1_linux_i686.tar.gz ; break ;;
  [Yy][Ee][Ss]) echo -n "Downloading Songbird from the internet--this could take several minutes, even on a broadband connection. Please be patient." ; wget -c http://download.songbirdnest.com/installer/linux/i686/Songbird_0_2_1_linux_i686.tar.gz ; echo -n "Unzipping the .tar.gz we downloaded." ; tar -xvzf Songbird_0_2_1_linux_i686.tar.gz ; break ;;
       N|n) echo -n "We have not properly detected your architecture. Songbird installation script quitting." ; exit ;;
  [Nn][Oo]) echo -n "We have not properly detected your architecture. Songbird installation script quitting." ; exit ;;
         *) echo -n "Invalid command. Please answer yes or no [y/n] " ;;
  esac
done
else
  echo "This script works for only x86 and AMD64 architectures."
  exit 1
fi
rm tmp.arch.txt
echo "
Moving Songbird to its own folder.
"
sudo mv Songbird /usr/local/bin/songbird
echo "
Removing the original .tar.gz
"
rm Songbird*.tar.gz
echo "
Making an executable for Songbird.
"
sudo ln -s /usr/local/bin/songbird/Songbird /usr/bin/Songbird
echo "
Downloading an icon for Songbird.
"
wget -c http://www.psychocats.net/ubuntu/songbirdicon.png
echo "
Putting the Songbird icon in the correct folder.
"
sudo mv songbirdicon.png /usr/share/pixmaps/songbird.png
echo "
Downloading the menu entry for Songbird.
"
wget -c http://www.psychocats.net/ubuntu/songbird.desktop
echo "
Moving the menu entry to the correct folder.
"
sudo mv songbird.desktop /usr/share/applications/songbird.desktop
echo "
After you refresh your menus, Songbird should be available as an application within the menus. If not, the launcher for Songbird should use the command Songbird (with a capital S).
"


```

---

### Post by japurcell on 2006-12-10
Latest version is here: [http://www.songbirdnest.com/thankyou/?sb_version=021&platform=linux-i686](http://www.songbirdnest.com/thankyou/?sb_version=021&platform=linux-i686)

---

### Post by bobbobbob on 2006-12-13
You asked to be informed of a version change, well it's happened, not a large change, but a change nonetheless.


Submitted by Aus on Wed, 11/29/2006 - 8:10pm.
The final version of 0.2.1 has just been released!

---

### Post by aysiu on 2006-12-13
> **bobbobbob said:**
> You asked to be informed of a version change, well it's happened, not a large change, but a change nonetheless.


Submitted by Aus on Wed, 11/29/2006 - 8:10pm.
The final version of 0.2.1 has just been released!
Okay. I've updated it. Anyone want to test?

---

### Post by ButteBlues on 2006-12-13
> **aysiu said:**
> Okay. I've updated it. Anyone want to test?
Sure, I'll play.

---

### Post by aysiu on 2006-12-13
Wait. Don't test it yet. I did something accidentally with the formatting. I'll post again when it's fixed.

---

### Post by aysiu on 2006-12-13
Never mind. It's working... at least for x86.

---

### Post by ButteBlues on 2006-12-13
> **aysiu said:**
> Never mind. It's working... at least for x86.
Indeed. ;)

There were a couple random errors, but it installed just fine.

---

### Post by machoo02 on 2007-02-09
This is one of the coolest apps that I've seen in a while.  Thanks Aysiu!

---

### Post by motang on 2007-02-16
Sweet thanks! :-D

---

### Post by OO7TDD on 2007-02-17
There is a new version out 0.2.5

[http://publicsvn.songbirdnest.com/trac/wiki/Nightly_Builds](http://publicsvn.songbirdnest.com/trac/wiki/Nightly_Builds)
or
[http://developer.songbirdnest.com/nightly/branch_builds/SONGBIRD_0_2/linux/i686/Songbird_0_2_5_20070214_linux-i686.tar.gz](http://developer.songbirdnest.com/nightly/branch_builds/SONGBIRD_0_2/linux/i686/Songbird_0_2_5_20070214_linux-i686.tar.gz)
[http://developer.songbirdnest.com/nightly/branch_builds/SONGBIRD_0_2/linux/x86_64/Songbird_0_2_5_20070214_linux-x86_64.tar.gz](http://developer.songbirdnest.com/nightly/branch_builds/SONGBIRD_0_2/linux/x86_64/Songbird_0_2_5_20070214_linux-x86_64.tar.gz)

They also began building nightly trunks

[http://developer.songbirdnest.com/nightly/builds/linux/i686](http://developer.songbirdnest.com/nightly/builds/linux/i686)
[http://developer.songbirdnest.com/nightly/builds/linux/x86_64](http://developer.songbirdnest.com/nightly/builds/linux/x86_64)

Thanks for the script, it is awesome.

---

### Post by ButteBlues on 2007-02-17
> **OO7TDD said:**
> There is a new version out 0.2.5

[http://publicsvn.songbirdnest.com/trac/wiki/Nightly_Builds](http://publicsvn.songbirdnest.com/trac/wiki/Nightly_Builds)
or
[http://developer.songbirdnest.com/nightly/branch_builds/SONGBIRD_0_2/linux/i686/Songbird_0_2_5_20070214_linux-i686.tar.gz](http://developer.songbirdnest.com/nightly/branch_builds/SONGBIRD_0_2/linux/i686/Songbird_0_2_5_20070214_linux-i686.tar.gz)
[http://developer.songbirdnest.com/nightly/branch_builds/SONGBIRD_0_2/linux/x86_64/Songbird_0_2_5_20070214_linux-x86_64.tar.gz](http://developer.songbirdnest.com/nightly/branch_builds/SONGBIRD_0_2/linux/x86_64/Songbird_0_2_5_20070214_linux-x86_64.tar.gz)

They also began building nightly trunks

[http://developer.songbirdnest.com/nightly/builds/linux/i686](http://developer.songbirdnest.com/nightly/builds/linux/i686)
[http://developer.songbirdnest.com/nightly/builds/linux/x86_64](http://developer.songbirdnest.com/nightly/builds/linux/x86_64)

Thanks for the script, it is awesome.
It is most definitely not released yet, so until it is, the script should still install 0.2.1.

---

### Post by RAV TUX on 2007-02-17
zero bugs listed for Linux?

surprising I thought Linux users would be the best at reporting bugs?

[http://bugzilla.songbirdnest.com/buglist.cgi?query_format=advanced&short_desc_type=allwordssubstr&short_desc=&product=Songbird&long_desc_type=substring&long_desc=&bug_file_loc_type=allwordssubstr&bug_file_loc=&status_whiteboard_type=allwordssubstr&status_whiteboard=&bug_status=NEW&bug_status=ASSIGNED&bug_status=REOPENED&op_sys=Linux&emailassigned_to1=1&emailtype1=substring&email1=&emailassigned_to2=1&emailreporter2=1&emailqa_contact2=1&emailcc2=1&emailtype2=substring&email2=&bugidtype=include&bug_id=&votes=&chfieldfrom=&chfieldto=Now&chfieldvalue=&cmdtype=doit&order=Reuse+same+sort+as+last+time&field0-0-0=longdesc&type0-0-0=greaterthan&value0-0-0=](http://bugzilla.songbirdnest.com/buglist.cgi?query_format=advanced&short_desc_type=allwordssubstr&short_desc=&product=Songbird&long_desc_type=substring&long_desc=&bug_file_loc_type=allwordssubstr&bug_file_loc=&status_whiteboard_type=allwordssubstr&status_whiteboard=&bug_status=NEW&bug_status=ASSIGNED&bug_status=REOPENED&op_sys=Linux&emailassigned_to1=1&emailtype1=substring&email1=&emailassigned_to2=1&emailreporter2=1&emailqa_contact2=1&emailcc2=1&emailtype2=substring&email2=&bugidtype=include&bug_id=&votes=&chfieldfrom=&chfieldto=Now&chfieldvalue=&cmdtype=doit&order=Reuse+same+sort+as+last+time&field0-0-0=longdesc&type0-0-0=greaterthan&value0-0-0=)
[IMG]http://img296.imageshack.us/img296/2799/newsabayon14ac6.png[/IMG]

---

### Post by Kuoi on 2007-02-18
Is there anybody who can install tar.gz files ?

It seems to me you need years of experience, or am I wrong ?
I want to test Songbird 2.5 tar.gz file , but can't install it.

I've tried > tar -xvvzf Songbird_0_2_5_20070214_linux-i686.tar.gz
cd Songbird_0_2_5_20070214_linux-i686
./configure
make
sudo make install but didn't work for me.

Kuoi

---

### Post by ButteBlues on 2007-02-18
> **Kuoi said:**
> Is there anybody who can install tar.gz files ?

It seems to me you need years of experience, or am I wrong ?
I want to test Songbird 2.5 tar.gz file , but can't install it.

I've tried  but didn't work for me.

Kuoi
Songbird isn't a typical source package in that it doesn't need compiling.

Just run:

```
/path/to/songbird/folder/Songbird/Songbird
```

eg.

```
/home/butteblues/Songbird/Songbird
```

---

### Post by Kuoi on 2007-02-19
Am I missing something ?

I'm running Songbird already , but wanted to test the Tar.gz files of the 2.5 version.

I've done > sudo /home/kuoi/Songbird_0_2_5_20070214_linux-x86_64.tar.gz
 , ... but that gives "command not find" .

I'm new to Linux , and like it a lot , but these Tar files ... Grrrr !

Kuoi

---

### Post by ButteBlues on 2007-02-19
> **Kuoi said:**
> Am I missing something ?

I'm running Songbird already , but wanted to test the Tar.gz files of the 2.5 version.

I've done  , ... but that gives "command not find" .

I'm new to Linux , and like it a lot , but these Tar files ... Grrrr !

Kuoi
A Tarball is a lot like a zip file - you have to extract the contents first.

```
tar -zxf Songbird_0_2_5_20070214_linux-x86_64.tar.gz
/home/kuoi/Songbird_0_2_5_20070214/Songbird
```

---

### Post by Kuoi on 2007-02-19
Thanks , it worked.

Running Songbird 2.5 for about 1 minute now :) 

Thanks for the help , Kuoi

---

### Post by Kuoi on 2007-02-19
Just 1 small question now ...

After checking , when I click on the usual link to Songbird it is still version 2.0.
Can I just copy and paste the new files from the tar to my Songbird directory , to make it 2.5 ?

Kuoi

---

### Post by Kuoi on 2007-02-19
It seems I'll stuck with 2 versions of Songbird , because I can't paste the files of 2.5 to my opt/songbird folder , or is there a command to do this ?

It is still better then 0 versions of Songbird , that's for sure ! :guitar: 

Kuoi

---

### Post by ButteBlues on 2007-02-19
> **Kuoi said:**
> It seems I'll stuck with 2 versions of Songbird , because I can't paste the files of 2.5 to my opt/songbird folder , or is there a command to do this ?

It is still better then 0 versions of Songbird , that's for sure ! :guitar: 

Kuoi
```
sudo cp /home/kuoi/Songbird_0_2_5_20070214 /opt
```

That should do the trick.

---

### Post by Kuoi on 2007-02-19
Can't make folder sudo /home/kuoi/Songbird_20070214 after i did > sudo cp /home/kuoi/Songbird_20070214 /opt

The output folder of the Tar was "/home/kuoi/Songbird_20070214" , and after I did your suggestion , and it didn't work , I've changed the name of the folder in the command , but that doesn't work to.

The errors are :

Or : "Can't change the rights of folder ..."
Or : "Can't make folder ..."

Sorry to disturb , Kuoi

---

### Post by banjobacon on 2007-02-19
> **Kuoi said:**
> Can't make folder sudo /home/kuoi/Songbird_20070214 after i did 

The output folder of the Tar was "/home/kuoi/Songbird_20070214" , and after I did your suggestion , and it didn't work , I've changed the name of the folder in the command , but that doesn't work to.

The errors are :

Or : "Can't change the rights of folder ..."
Or : "Can't make folder ..."

Sorry to disturb , Kuoi

Try:
```
sudo cp -r /path/to/songbird /opt
```

---

### Post by OO7TDD on 2007-02-19
> **ButteBlues said:**
> It is most definitely not released yet, so until it is, the script should still install 0.2.1.

I guess its not an actual release but it is out under nightly.

For all those who want to try to new nightly you can get it here
[http://developer.songbirdnest.com/nightly/branch_builds/SONGBIRD_0_2/linux/x86_64/](http://developer.songbirdnest.com/nightly/branch_builds/SONGBIRD_0_2/linux/x86_64/)

To replace the 0.2.1, simply copy the contents of the folder inside the tarball to

/usr/local/bin/songbird/

as that is where the install script for 0.2.1 installs 0.2.1
the links in your application menu and 'Songbird' from command line will still work.

I did this with the Feb 19th build and all is well.

---

### Post by hammadr89 on 2007-03-02
It's been updated to .25 now

---

### Post by aysiu on 2007-03-02
> **hammadr89 said:**
> It's been updated to .25 now
I'll have the script updated within a day or two. If not, then please remind me again by posting in this thread. Thanks for the heads-up.

---

### Post by aysiu on 2007-03-02
Okay. It's updated now, but it's not tested.

Can someone who does not yet have it installed test out the script and post back a confirmation that it works... or doesn't?

---

### Post by Kuoi on 2007-03-02
Thank you !

It works , and this is the first script that works for me .
The older ones gave me always one or an other error , but the 2.5 script is working fine !

At last I have Songbird 2.5 when I click "Help" > "about"  .

Many many thanks , Kuoi

=D>

---

### Post by aysiu on 2007-03-02
Glad it worked for you, Kuoi.

And thanks for being a tester!

---

### Post by Kuoi on 2007-03-02
I love to test software.

And after I had an issue with Firefox , I just saw 5 minutes ago that you also had a script for Firefox.

Installed , and works fine now , without issues.
I just had to install it twice , after I selected the location BE , which I thought was Belgium ... It Isn't !
I did the install again but selected NL , because we Belgians  read and write Dutch .
My mistake .

A thanks again to you for the working Firefox !

Kuoi

---

### Post by aysiu on 2007-03-02
Well, in all fairness, I have a page dedicated to the Firefox script and I wrote the original script the current script is based on, but most of the work put into making the script what it is today was done by another forum member named *nanotube*.

---

### Post by Kuoi on 2007-03-03
Guess what ...

I've started up my computer , after I had some sleep.

I've started Songbird a minute ago , and I saw it directly...
It was scanning for plugins or something , and then I know enough... it's back to version 0.2 again !!!

I love Ubuntu much , but as a software tester I can say 1 thing  ...[I][U] Linux is killing me !!!!
[/U][/I]
Why , tell me why I always get that version 0.2 again ?
Grrrr !

I used in Windooos to test software , but Linux doesn't let me doing my thung.

If it isn't updated through the automatic update future , just forget it !  ... that's my feeling right now.

Kuoi

---

### Post by roderikk on 2007-03-03
Hm, strange because the update here went flawlessly. I just had to be a bit patient when Songbird started up after the update because it was downloading and installing the new plugin infrastructure.

On a whole other note, I do really need to get used to the way songbird handles stuff and am currently just back at my good old amarok. Now if they would just implement the playing of movies and streams I would be happy... (of course optionally because I am aware that some people just want a audio player and not a complete media centre...).

---

### Post by Kuoi on 2007-03-03
I think it has to do something with the 'starter'.
When I usqe the one on my desktop , it goes back to 0.2 , but when I use the starter in "audio and video" , all goes well , and it's 2.5 .

I've replaced the starter on my desktop with a new one , and all seems ok .

It must be an old starter from the old script or so that didn't work well.
Let's hope and see in the near future if it stays 2.5.

Kuoi

---

### Post by BOBSONATOR on 2007-03-05
sweet, but unfortunatley it crashes whenever i try to play a song..

---

### Post by geckorock69 on 2007-03-11
Downloaded the script, followed the instructions, all is well. Thank you!

---

### Post by Kabamaru on 2007-03-16
FYI: Version 0.2.5.1 is available.

Thanks for having the script up at all.

---

### Post by aysiu on 2007-03-16
> **Kabamaru said:**
> FYI: Version 0.2.5.1 is available.

Thanks for having the script up at all.
Not according to the Songbird website... at least as far as I can see.

Can you provide a link?

---

### Post by Kabamaru on 2007-03-16
> **aysiu said:**
> Not according to the Songbird website... at least as far as I can see.

Can you provide a link?

I didn't find out on the site.  I ran a search for update via Songbird itself, and it noted that a new version was available.  I installed it through that dialog window (simple point and click), so I'm not sure where it would be on the site itself.

---

### Post by Kabamaru on 2007-03-22
I'm wondering if 0.2.5.1 is just an rc?
[http://download.songbirdnest.com/installer/linux/i686/](http://download.songbirdnest.com/installer/linux/i686/)
A really late reply, I know.  This has just been bugging me for the past few days.

In any case, it doesn't really matter.

---

### Post by J-Red on 2007-03-27
This does not seem to work for me. I just downloaded it from the Songbird Site and it installs with no errors, but the command "Songbird" and from the menu do not work.

---

### Post by FuturePilot on 2007-03-27
Wow! Thanks aysiu! It worked perfectly. I've always wanted to try out Songbird but was never sure about installing it.:)

---

### Post by tomservo291 on 2007-03-27
My install fails... Even as running as su.

I was trying to install myself before this, and now tried this script thinking it may meet some dependency I didn't find.  Here is a snippet of what I get:

alex@themoon:~/Desktop$ Songbird 
*** UPLOADING METRICS ***
(Gecko:21364): Gdk-CRITICAL **: _gdk_window_destroy_hierarchy: assertion `window != NULL' failed

(Gecko:21364): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(Gecko:21364): Gdk-CRITICAL **: _gdk_window_destroy_hierarchy: assertion `window != NULL' failed

(Gecko:21364): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(Gecko:21364): Gdk-CRITICAL **: _gdk_window_destroy_hierarchy: assertion `window != NULL' failed

(Gecko:21364): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int)3

(Gecko:21364): Gdk-CRITICAL **: _gdk_window_destroy_hierarchy: assertion `window != NULL' failed

(Gecko:21364): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(Gecko:21364): Gdk-CRITICAL **: _gdk_window_destroy_hierarchy: assertion `window != NULL' failed

(Gecko:21364): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(Gecko:21364): Gdk-CRITICAL **: _gdk_window_destroy_hierarchy: assertion `window != NULL' failed

(Gecko:21364): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int)3

(Gecko:21364): Gdk-CRITICAL **: _gdk_window_destroy_hierarchy: assertion `window != NULL' failed

---

### Post by joshier on 2007-04-01
Worked for me.. thanks.

---

### Post by aysiu on 2007-04-24
I've moved the script and instructions to the Wiki:
[https://help.ubuntu.com/community/Songbird](https://help.ubuntu.com/community/Songbird)

Now anyone can edit it whenever the new version comes out.

---

### Post by justin whitaker on 2007-04-24
> **aysiu said:**
> I've moved the script and instructions to the Wiki:
[https://help.ubuntu.com/community/Songbird](https://help.ubuntu.com/community/Songbird)

Now anyone can edit it whenever the new version comes out.

You are the...cat thingy! :)

---

### Post by Kuoi on 2007-05-16
Just to let you know that I've received an error every time I did tried the command > ./installsongbird.sh

The error was something like "/bin/bash file or folder does not excists."

After comparing the old script with the new one on the wiki site , I've changed the first sentence for the new script from > #!/bin/bash (-)
to > #!/bin/bash

After that ,  Songbird installed without any error , and is working fine here .

I don't know why I had the error , but just wanted to let you know that this method have fixed it.

Thanks for the script , Kuoi

---

### Post by aysiu on 2007-05-16
I don't know how to get the ```
(-)
``` off the Wiki page.

Any Wiki gurus out there know how to fix it?
[https://help.ubuntu.com/community/Songbird](https://help.ubuntu.com/community/Songbird)

---

### Post by MissG on 2007-06-08
Script worked great for me. Thank you aysiu!

---

### Post by Spike-X on 2007-06-11
Thanks for this script! It worked 100% once I removed that pesky (-) thingy.

---

### Post by TheeMahn2003 on 2007-07-03
> **aysiu said:**
> I just created an installation script for Songbird 0.2, in case anyone's interested.

The instructions and script can be found here:
[http://www.psychocats.net/ubuntu/songbird](http://www.psychocats.net/ubuntu/songbird)

The script is for x86, not AMD64.

Much better then my [rmod]("http://ubuntusoftware.info/rmods/mod-install-songbird.rmod") ;), as of version .2 downloaded the tar and built it OS specific, I now count on the repo. I should spend that kinda time with each script I write... hats off brother... All I currently look for is a script that just works let the repos handle it in the end.  Do you mind if I borrow your code?   I'm sure what I ask should have some meaning coming from me, I have written my current script based on allowing updating via repo as of current, but you do so specific, and do a great job likewise.

In conclusion keep up the good work, I will not add it w/o your personal say so.  Same so as [tseliot]("http://www.albertomilone.com/nvidia_scripts1.html") with envy. I ask you the same permission.  Irregardless of your answer in what I ask, keep up the great work brother.

Best regards,

TheeMahn

---

### Post by aysiu on 2007-07-03
The code for that script is open source. In fact, many components of that script are lifted straight off *nanotube's* Firefox installation script.

P.S. To the forum dwellers, I am not officially back. I have been lurking every now and then just to see how the forums are doing. I do plan to come back from my break at some point, but it'll be much later. Hope you all are doing well.

---

### Post by retro_killa on 2007-07-05
i just d/l & installed songbird & the looks are very eye poping. but still wheni went to shoutcast and tryed to stream live net radio i got any error :( cant wait for the real app to be 100% working

---

### Post by narehart on 2007-07-10
Hey I used your script and songbird installed nicely.  There is one little problem however. If I close the program and then try to open it again it tells me that songbird is still running but I can't find an Icon in my system tray or see songbird listed in my running processes. This probably has nothing to do with your script but some help would be greatly appreciated.

---

### Post by aysiu on 2007-07-10
I don't actually use Songbird, but I'd image ```
killall Songbird
``` ```
killall songbird
``` or ```
killall songbird-bin
``` might do the trick.

---

### Post by narehart on 2007-07-10
thnx

---

### Post by aysiu on 2007-07-10
> **narehart said:**
> thnx
Which one worked?

---

### Post by narehart on 2007-07-10
Actually, it's now closing completely when I choose quit. Weird, huh?

---

### Post by aysiu on 2007-07-10
There was probably just one lingering bad Songbird session out there.

---

### Post by Spike-X on 2007-07-11
I get the same bug when I try to install an extension, then click 'Restart Songbird'. I guess they'll fix it soon enough.

---

### Post by MadMarv on 2007-07-17
Hi, Aysiu - thanks for the script. Works great, just like all your how-tos/ aids. Buggy or not, this is a great player.

---

### Post by CloCkWeRX on 2007-08-01
It would be really neat to have all of the file locations extracted out to somewhere easy to edit.

That would allow me to swap easily from "installsongbird.sh" to a "installnightlies.sh"...

---

### Post by javaJake on 2007-10-06
[color=grey]The script is installing an old version now. Update is appreciated. :) [/color] Never mind, 0.2.5 is the newest. What's odd is an extension complained it'll only work in 0.3.X

BTW, the script works as-is! Thanks!

---

### Post by PapoticoUS on 2007-10-21
There's a newer version available right now: Songbird 0.3 Release Candidate 1

If you could please update the script so we could be able to download this new version.

Thanks ahead of time. Newbie Out...

---

### Post by zaknafein99 on 2007-10-26
RC3 just came out, could you make the script for install this version, I can't make the site download work. The executable does nothing.

Thanks

---

### Post by aysiu on 2007-10-26
The front page of Songbird still says 0.2.5

---

### Post by fluteflute on 2007-10-27
It is because 0.3 is currently at release candidate 2 stage. If you scroll down the front page to the bloggy bit you can see the latest version. They say 0.3 final will be released soon though.

---

### Post by aysiu on 2007-10-27
Well, when release 0.3 is final, I'll update the script.

Actually, if someone actually knows how to write scripts (hint, hint: I don't), I'm sure she or he could come up with a way for the script to automatically pull the latest version of Songbird so that the script does not need to be updated manually.

---

### Post by Martje_001 on 2007-10-27
> **aysiu said:**
> Well, when release 0.3 is final, I'll update the script.

Actually, if someone actually knows how to write scripts (hint, hint: I don't), I'm sure she or he could come up with a way for the script to automatically pull the latest version of Songbird so that the script does not need to be updated manually.
Well that's quite easy ;).

pm me if you interested.

---

### Post by aysiu on 2007-10-27
> **Martje_001 said:**
> Well that's quite easy ;).

pm me if you interested.
The Songbird script is open source. Feel free to modify it as you see fit.
[https://help.ubuntu.com/community/Songbird](https://help.ubuntu.com/community/Songbird)

---

### Post by Martje_001 on 2007-10-27
May I make it graphical?

---

### Post by aysiu on 2007-10-27
> **Martje_001 said:**
> May I make it graphical?
By all means!

---

### Post by Neo4 on 2007-10-27
can anyone tell me how do I put the Album applet working on the 0.3rc? i have shockwave plugin and javascript debugger but in [www.java.com](www.java.com) if i click on see if java is installed it says no... 
but on firefox says yes.

thanks

---

### Post by javaJake on 2007-10-27
> **Neo4 said:**
> can anyone tell me how do I put the Album applet working on the 0.3rc? i have shockwave plugin and javascript debugger but in [www.java.com](www.java.com) if i click on see if java is installed it says no... 
but on firefox says yes.

thanks

This is off-topic and will end up hijacking (changing the topic of) this thread. Please post your support request in the proper site/forum to get better help. Thank you.

---

### Post by macogw on 2007-10-27
> **croak77 said:**
> Is Songbird actually worth installing now or wait until it gets closer to 1.0?
It works well.  It lacks album art support, though, and when it watches a folder for new music, it doesn't do subdirectories.

---

### Post by Martje_001 on 2007-10-28
I've made to script (please test them):

**To install Songbird:**
```
#!/bin/bash
if [ -d /usr/local/bin/songbird ]; then
    zenity --info --text="You appear to already have Songbird installed. To get the newest version, you should use the         self-update function in Songbird instead of using this script."
    exit
fi

cd /tmp
uname -m > tmp.arch.txt
if grep -q "64" tmp.arch.txt ; then
    anw=`zenity --question --text "You appear to have an AMD64 architecture. Do you want to install the 64-bit version of Songbird?"; echo $?`
    if [ $anw = 0 ] ; then
    gksudo "echo 0"
    wget http://www.xs4all.nl/~mgj1/Songbird/64.bit
    URL=`head -n 1 64.bit | tail -n 1`
    FILE=`head -n 2 64.bit | tail -n 1`
    rm 64.bit
    wget "$URL" 2>&1 | sed -u 's/.*\ \([0-9]\+%\)\ \+\([0-9.]\+\ [KMB\/s]\+\)$/\1\n# Downloading Songbird with \2/' | zenity --progress --auto-close --title="Downloading Songbird..."
    tar -xvzf "$FILE"
    else
    zenity --info --text="Installation cancelled."
    fi

elif grep -q "86" tmp.arch.txt ; then
    anw=`zenity --question --text "You appear to have an x86 architecture. Do you want to install the i686 version of Songbird?"; echo $?`
    if [ $anw = 0 ] ; then
    gksudo "echo 0"
    wget http://www.xs4all.nl/~mgj1/Songbird/32.bit
    URL=`head -n 1 32.bit | tail -n 1`
    FILE=`head -n 2 32.bit | tail -n 1`
    rm 32.bit
    wget "$URL" 2>&1 | sed -u 's/.*\ \([0-9]\+%\)\ \+\([0-9.]\+\ [KMB\/s]\+\)$/\1\n# Downloading Songbird with \2/' | zenity --progress --auto-close --title="Downloading Songbird..."
    tar -xvzf "$FILE"
    else
    zenity --info --text="Installation cancelled."
    fi
else
    zenity --info --text="This script works for only x86 and AMD64 architectures."
fi
rm tmp.arch.txt
gksudo "mv Songbird /usr/local/bin/songbird"
rm Songbird*.tar.gz
gksudo "ln -s /usr/local/bin/songbird/Songbird /usr/bin/Songbird"
wget -c -q http://www.psychocats.net/ubuntu/songbirdicon.png
gksudo "mv songbirdicon.png /usr/share/pixmaps/songbird.png"
wget -c -q http://www.psychocats.net/ubuntu/songbird.desktop
gksudo "mv songbird.desktop /usr/share/applications/songbird.desktop"
zenity --info --text="After you refresh your menus, Songbird should be available as an application within the menus. If not, the launcher for Songbird should use the command Songbird (with a capital S). \n \nEnjoy!"
```**To remove Songbird:**
```
#!/bin/bash
anw=`zenity --question --text "This will remove Songbird. Continue?"; echo $?`
if [ $anw = 0 ] ; then
    gksudo "rm -rf /usr/local/bin/songbird"
    gksudo "rm /usr/bin/Songbird"
    gksudo "rm /usr/share/applications/songbird.desktop"
    gksudo "rm /usr/share/pixmaps/songbird.png"
    anw=`zenity --question --text "Do you want to keep your preferences?"; echo $?`
    if [ $anw = 1 ] ; then
    rm -r ~/.songbird
    fi
fi
zenity --info --text="Songbird is now removed from your system."
```

---

### Post by Soarer on 2007-10-28
The install script works fine for me on Gutsy 64bit.

Thanks :)

---

### Post by Martje_001 on 2007-10-28
Script can be downloaded from **"[Here (Install Songbird)]("http://www.xs4all.nl/~mgj1/Songbird/installsongbird.sh")"** and "[B][And here (remove Songbird)]("http://www.xs4all.nl/~mgj1/Songbird/removesongbird.sh")"

[/B]Here are the instructions:
[IMG]http://www.xs4all.nl/%7Emgj1/Songbird/Screenshot-opening%20installsongbird.png[/IMG]
[IMG]http://www.xs4all.nl/%7Emgj1/Songbird/Screenshot.png[/IMG]
[IMG]http://www.xs4all.nl/%7Emgj1/Songbird/Screenshot-installsongbird.png[/IMG]

Double click on the script
[IMG]http://www.xs4all.nl/%7Emgj1/Songbird/Screenshot-nautilus.png[/IMG]
I will host the images! Thank you!

---

### Post by bigcat42 on 2007-11-01
FYI, Songbird 0.3 has been released.

---

### Post by aysiu on 2007-11-01
> **bigcat42 said:**
> FYI, Songbird 0.3 has been released.
It'd be great if you and a bunch of other Songbird users could test Martje_001's script to see if it picks up the latest version.

If so, we can edit the Wiki to include that script instead of my to-be-manually-updated script.

---

### Post by Soarer on 2007-11-01
Firstly, the script tells you that Songbird is already installed, and to use the update function in Songbird. According to that, there were no updates.

So I used the 'remove' script, and ran the 'install' script whereupon it installed 2.5.1 again.

I am running 64bit, so there may not be an update for that, but in my case it didn't work.

---

### Post by aysiu on 2007-11-01
> **Soarer said:**
> Firstly, the script tells you that Songbird is already installed, and to use the update function in Songbird. According to that, there were no updates.

So I used the 'remove' script, and ran the 'install' script whereupon it installed 2.5.1 again.

I am running 64bit, so there may not be an update for that, but in my case it didn't work.
This is Martje_001's script, not the one currently on the Wiki, right?

---

### Post by Soarer on 2007-11-01
The one on this thread is the one I used (I don't know this Wiki of which you speak)

:)

---

### Post by Dale61 on 2007-11-01
Have been a Songbird user since v0.1, and now up to 0.2.5.1

Never have had a problem with it, but I followed an install how-to from elsewhere.

Not taking anything away from aysiu's effort, but when I installed Songbird, the directory ended up in the /opt folder.

Here's the how-to I used:
[http://www.arsgeek.com/?p=615]("http://www.arsgeek.com/?p=615")

I have found Songbird to be less CPU intensive than anything else for Ubuntu, but I currently only have 306 mp3 tracks in the library, which play in random mode.  However, I don't use it as a browser, just a music player.

---

### Post by Martje_001 on 2007-11-01
[SIZE=4]****My script now downloads 3.0***[/SIZE]

---

### Post by oozzo on 2007-11-01
Thank you very much Aysiu! I know its still in beta, but im actually very impressed by this program as compared to some of the alternatives. I think the commercial release is going to grab a large fan base.

---

### Post by Martje_001 on 2007-11-03
I don't like Songbird 3.I hate the default feather](*,), and no other are available:mad:

---

### Post by 43moon on 2007-11-04
Install went without a hitch.  Thanks Martje_001 and everyone else in the scene.  People like you and aysiu are why I love being an Ubuntu user.

---

### Post by smartboyathome on 2007-11-05
> **Martje_001 said:**
> Script can be downloaded from **"[Here (Install Songbird)]("http://www.xs4all.nl/~mgj1/Songbird/installsongbird.sh")"** and "[B][And here (remove Songbird)]("http://www.xs4all.nl/~mgj1/Songbird/removesongbird.sh")"

[/B]Here are the instructions:
<snip>
I will host the images! Thank you!

This worked great! Thank you! One suggestion: How about a "Installing Songbird" status bar after the downloading songbird one? There was a big gap between that and the end one.

---

### Post by Larsewitsch on 2007-11-06
> **aysiu said:**
> I just created an installation script for Songbird 0.2, in case anyone's interested.

The instructions and script can be found here:
[http://www.psychocats.net/ubuntu/songbird](http://www.psychocats.net/ubuntu/songbird)

The script is for x86, not AMD64.

Sonbird 0.3 has appeared ,please change the sript! Thanks!

---

### Post by aysiu on 2007-11-06
> **Martje_001 said:**
> [SIZE=4]****My script now downloads 3.0***[/SIZE]
I've updated the Wiki to use your new script, Martje_001.

I've also changed the Psychocats link to redirect to the Wiki.

---

### Post by Martje_001 on 2007-11-10
> **aysiu said:**
> I've updated the Wiki to use your new script, Martje_001.

I've also changed the Psychocats link to redirect to the Wiki.
OK, thanx :)

---

### Post by Spike-X on 2007-11-11
Just so you know, the script worked flawlessly for me (Gutsy AMD_64).

Unfortunately, the program itself still needs a lot of work.

---

### Post by zero456 on 2008-01-08
Songbird 0.4 has been released.  Any chance on updating the script?

---

### Post by Martje_001 on 2008-01-09
> **zero456 said:**
> Songbird 0.4 has been released.  Any chance on updating the script?
Done.

---

### Post by Neo4 on 2008-01-09
I've installed this new sondbird and now i can't play any music files, and my library just disapeared...

anyone can help me?

---

### Post by perlluver on 2008-01-09
> /bin/bash: (-): No such file or directory
 I am getting this trying to install from the script.

Edit:  I took out the (-) after /bin/bash and it works fine.

---

### Post by perlluver on 2008-01-09
Here is the new script:

```
#!/bin/bash
if [ -d /usr/local/bin/songbird ]; then
        zenity --info --text="You appear to already have Songbird installed. To get the newest version, you should use the              self-update function in Songbird instead of using this script."
        exit
fi

cd /tmp
uname -m > tmp.arch.txt
if grep -q "64" tmp.arch.txt ; then
        anw=`zenity --question --text "You appear to have an AMD64 architecture. Do you want to install the 64-bit version of Songbird?"; echo $?`
        if [ $anw = 0 ] ; then
        gksudo "echo 0"
        wget http://www.xs4all.nl/~mgj1/Songbird/64.bit
        URL=`head -n 1 64.bit | tail -n 1`
        FILE=`head -n 2 64.bit | tail -n 1`
        rm 64.bit
        wget "$URL" 2>&1 | sed -u 's/.*\ \([0-9]\+%\)\ \+\([0-9.]\+\ [KMB\/s]\+\)$/\1\n# Downloading Songbird with \2/' | zenity --progress --auto-close --title="Downloading Songbird..."
        tar -xvzf "$FILE"
        else
        zenity --info --text="Installation cancelled."
        fi

elif grep -q "86" tmp.arch.txt ; then
        anw=`zenity --question --text "You appear to have an x86 architecture. Do you want to install the i686 version of Songbird?"; echo $?`
        if [ $anw = 0 ] ; then
        gksudo "echo 0"
        wget http://www.xs4all.nl/~mgj1/Songbird/32.bit
        URL=`head -n 1 32.bit | tail -n 1`
        FILE=`head -n 2 32.bit | tail -n 1`
        rm 32.bit
        wget "$URL" 2>&1 | sed -u 's/.*\ \([0-9]\+%\)\ \+\([0-9.]\+\ [KMB\/s]\+\)$/\1\n# Downloading Songbird with \2/' | zenity --progress --auto-close --title="Downloading Songbird..."
        tar -xvzf "$FILE"
        else
        zenity --info --text="Installation cancelled."
        fi
else
        zenity --info --text="This script works for only x86 and AMD64 architectures."
fi
rm tmp.arch.txt
gksudo "mv Songbird /usr/local/bin/songbird"
rm Songbird*.tar.gz
gksudo "rm /usr/bin/Songbird"
gksudo "rm -r /usr/bin/Songbird"
gksudo "ln -s /usr/local/bin/songbird/songbird /usr/bin/Songbird"
wget -c -q http://www.psychocats.net/ubuntu/songbirdicon.png
gksudo "mv songbirdicon.png /usr/share/pixmaps/songbird.png"
wget -c -q http://www.psychocats.net/ubuntu/songbird.desktop
gksudo "mv songbird.desktop /usr/share/applications/songbird.desktop"
zenity --info --text="After you refresh your menus, Songbird should be available as an application within the menus. If not, the launcher for Songbird should use the command Songbird (with a capital S). \n \nEnjoy!"
```

---

### Post by Martje_001 on 2008-01-10
> **Neo4 said:**
> I've installed this new sondbird and now i can't play any music files, and my library just disapeared...

anyone can help me?
That's because the new version is not compatible with older versions. Remove **.songbird** or** .songbird1**

---

### Post by tigerplug on 2008-01-10
> **aysiu said:**
> I just created an installation script for Songbird 0.2, in case anyone's interested.

The instructions and script can be found here:
[http://www.psychocats.net/ubuntu/songbird](http://www.psychocats.net/ubuntu/songbird)

The script is for x86, not AMD64.

I don't mean to be rude in anyway. But, what is the difference between installing it this way and installing it from [http://www.getdeb.net/](http://www.getdeb.net/) ?

---

### Post by Neo4 on 2008-01-10
> **Martje_001 said:**
> That's because the new version is not compatible with older versions. Remove **.songbird** or** .songbird1**

yes you hare right!

thanks a lot!

---

### Post by jeyaganesh on 2008-01-10
Thanks to 'Perlluver' for Songbird new script. 
My very special thanks to 'Ayisu' for not only starting this thread also for his very patient support to new ubuntu users through lot of 'how-to-threads'.:)

Kind Regards
Jay

---

### Post by breakerr on 2008-01-10
I dont know what Im doing wrong but it looks is something stupid...I went to my add/remove and removed the old previous songbird on my Pc the **_0.2.5_** and I tried several ways to install the new one and is up and running normally but I can only open it by going to terminal and*** sudo nautilus*** and then I go into directory  **opt/songbird** and click on the songbird icon to run it...but if I try by going to the icon I created on the menu under  _Applications/sound and video/songbird_ I get nothing...no matter how much I edit the directory root to reach the file or if I try going directly into the folder without typing sudo nautilus from terminal I cant get it to run from there either. What Im doing wrong ????

I used this guide  [http://www.ubuntugeek.com/install-songbird-music-player-in-ubuntu.html](http://www.ubuntugeek.com/install-songbird-music-player-in-ubuntu.html)  I just changed the version number.

---

### Post by E Double on 2008-01-19
When I use the Songbird .4 install script the application installs and runs, but is waay too large for my display.  There is no way that I can see to reduce its scale.  Everything is HUGE-buttons everything.  My screen resolution is 1680x1050. Any help would be greatly appreciated.

                                    Cheers,

                                         D

---

### Post by Martje_001 on 2008-01-19
> **jeyaganesh said:**
> Thanks to 'Perlluver' for Songbird new script.
That's my script actually =(. Perlluver only deleted a typo...

> When I use the Songbird .4 install script the application installs and runs, but is waay too large for my display. There is no way that I can see to reduce its scale. Everything is HUGE-buttons everything. My screen resolution is 1680x1050. Any help would be greatly appreciated.
Can you post a screenshot?

---

### Post by rasmusbp on 2008-02-25
hi. i'm having trouble with the script - I hope someone can help! everything seems to be fine during installation, it downloads, installs, and I get no error messages. However, Songbird won't start when I type "Songbird" in a terminal. I get

> bash: Songbird: command not found

Also, if I do a search on my File System, I don't see program files anywhere. (see attached).

Please help... :)

All the best,
Rasmus, Copenhagen.

---

### Post by Martje_001 on 2008-02-25
It's in your menu too, applications --> Multimedia (or how is it called in english?) --> Songbird

and, if you typ songbird (without capital s)?

---

### Post by rasmusbp on 2008-02-25
thanks for the reply martje. the menu shortcut is there (in "sound and video"), but doesn't work either. Nothing happens. And nothing happens with songbird or Songbird, which ever way you spell it... 

Is there a "log" of some kind from the installation process? As far as I can tell from the script, the program files are supposed to go in usr/local/bin - but as you can see from the screendump, that library doesn't exist?! For the same reason, I guess, the link in usr/bin is listed as "broken" (see the other dump)

thanks again for any help!  ;)

best
Rasmus.

---

### Post by Martje_001 on 2008-02-25
What's the output of:
```
wget -c http://www.xs4all.nl/~mgj1/Songbird/installsongbird.sh
chmod +x installsongbird.sh
./installsongbird.sh
```
?

---

### Post by rasmusbp on 2008-02-25
I post the whole thing below. I think the problem may be connected to the line: 

> cannot move `Songbird' to `/usr/local/bin/songbird': No such file or directory

there's also a problem with my Blubuntu installation?! (

thanks again

rasmus.



> 

100%[====================================>] 116           --.--K/s             

21:18:57 (5.58 MB/s) - `32.bit' saved [116/116]

/usr/share/themes/Blubuntu/gtk-2.0/gtkrc:169: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
Songbird/
Songbird/application.ini
Songbird/chrome/
Songbird/chrome/icons/
Songbird/chrome/icons/default/
Songbird/chrome/icons/default/default.xpm
Songbird/chrome/songbird.manifest
Songbird/chrome/browser.manifest
Songbird/chrome/browser.jar
Songbird/chrome/songbird.jar
Songbird/chrome/rubberducky.manifest
Songbird/chrome/rubberducky.jar
Songbird/chrome/locales.manifest
Songbird/chrome/locales.jar
Songbird/components/
Songbird/components/fuel.xpt
Songbird/components/fuelApplication.js
Songbird/components/nsSearchService.js
Songbird/components/nsSearchSuggestions.js
Songbird/components/browsersearch.xpt
Songbird/components/nsSidebar.js
Songbird/components/nsBrowserGlue.js
Songbird/components/browsercompsbase.xpt
Songbird/components/sbWidgets.xpt
Songbird/components/sbAddonMetadata.js
Songbird/components/sbBundle.xpt
Songbird/components/sbBundle.js
Songbird/components/sbCommandLine.xpt
Songbird/components/sbCommandLine.js
Songbird/components/sbPlaylistPlayback.xpt
Songbird/components/sbPlaylistPlayback.js
Songbird/components/sbMediaContentListener.js
Songbird/components/sbMediaSniffer.so
Songbird/components/sbController.xpt
Songbird/components/sbDataRemote.xpt
Songbird/components/sbDataRemote.js
Songbird/components/sbDatabaseEngine.xpt
Songbird/components/sbDBEngine.so
Songbird/components/sbSQLBuilder.xpt
Songbird/components/sbSQLBuilder.so
Songbird/components/sbDOMEventUtils.xpt
Songbird/components/sbDOMEventUtils.so
Songbird/components/sbProperties.xpt
Songbird/components/sbProperties.so
Songbird/components/sbProperties.jsm
Songbird/components/sbLibraryBase.xpt
Songbird/components/sbLibraryUtils.jsm
Songbird/components/sbStorageFormatter.jsm
Songbird/components/sbLibraryManager.so
Songbird/components/sbLocalDatabaseLibrary.xpt
Songbird/components/sbLocalDatabaseDynamicPlaylist.js
Songbird/components/sbLocalDatabaseLibrary.so
Songbird/components/sbMetadataManager.xpt
Songbird/components/sbMetadataManager.so
Songbird/components/sbMetadataHandlerTaglib.xpt
Songbird/components/sbMetadataHandlerTaglib.so
Songbird/components/sbGStreamer.xpt
Songbird/components/sbGStreamer.so
Songbird/components/sbDeviceBase.xpt
Songbird/components/sbDeviceManager.xpt
Songbird/components/sbDeviceManager.so
Songbird/components/sbDownloadDevice.xpt
Songbird/components/sbDownloadDevice.so
Songbird/components/sbAutoDownloader.js
Songbird/components/sbDownloadDeviceHelper.js
Songbird/components/sbDownloadDeviceServicePaneModule.js
Songbird/components/sbDisplayPanes.xpt
Songbird/components/sbDisplayPanes.js
Songbird/components/sbDragAndDrop.xpt
Songbird/components/sbDndSourceTracker.js
Songbird/components/sbFaceplate.xpt
Songbird/components/sbFaceplateManager.js
Songbird/components/sbFeathers.xpt
Songbird/components/sbFeathersManager.js
Songbird/components/sbFileScan.xpt
Songbird/components/sbFileScan.so
Songbird/components/sbIntegration.xpt
Songbird/components/sbIntegration.so
Songbird/components/sbHotkeyActions.js
Songbird/components/ArrayConverter.jsm
Songbird/components/XPCOMUtils.jsm
Songbird/components/sbMetrics.xpt
Songbird/components/sbMetrics.js
Songbird/components/sbPlaylistCommands.xpt
Songbird/components/sbPlaylistCommands.so
Songbird/components/sbPlaylistCommandsBuilder.js
Songbird/components/sbPublicPlaylistCommands.js
Songbird/components/sbAddToPlaylist.jsm
Songbird/components/kPlaylistCommands.jsm
Songbird/components/sbPlaylistReader.xpt
Songbird/components/sbPlaylistHandlerModule.js
Songbird/components/sbPlaylistReaderManager.js
Songbird/components/sbPlaylistReaderListener.js
Songbird/components/sbBrowserAPI.xpt
Songbird/components/sbBrowserAPI.so
Songbird/components/sbSearchSuggester.js
Songbird/components/sbServicePane.xpt
Songbird/components/sbServicePaneService.js
Songbird/components/sbBookmarksService.js
Songbird/components/sbLibraryServicePaneService.js
Songbird/components/sbState.xpt
Songbird/components/sbParserError.js
Songbird/defaults/
Songbird/defaults/preferences/
Songbird/defaults/preferences/songbird-prefs.js
Songbird/defaults/preferences/songbird-channel-prefs.js
Songbird/defaults/profile/
Songbird/defaults/profile/mimeTypes.rdf
Songbird/extensions/
Songbird/extensions/{f13b157f-b174-47e7-a34d-4815ddfdfeb8}/
Songbird/extensions/{f13b157f-b174-47e7-a34d-4815ddfdfeb8}/chrome/
Songbird/extensions/{f13b157f-b174-47e7-a34d-4815ddfdfeb8}/chrome/venkman.jar
Songbird/extensions/{f13b157f-b174-47e7-a34d-4815ddfdfeb8}/components/
Songbird/extensions/{f13b157f-b174-47e7-a34d-4815ddfdfeb8}/components/venkman-service.js
Songbird/extensions/{f13b157f-b174-47e7-a34d-4815ddfdfeb8}/chrome.manifest
Songbird/extensions/{f13b157f-b174-47e7-a34d-4815ddfdfeb8}/install.rdf
Songbird/extensions/inspector@mozilla.org/
Songbird/extensions/inspector@mozilla.org/platform/
Songbird/extensions/inspector@mozilla.org/platform/Linux/
Songbird/extensions/inspector@mozilla.org/platform/Linux/chrome/
Songbird/extensions/inspector@mozilla.org/platform/Linux/chrome/icons/
Songbird/extensions/inspector@mozilla.org/platform/Linux/chrome/icons/default/
Songbird/extensions/inspector@mozilla.org/platform/Linux/chrome/icons/default/winInspectorMain.xpm
Songbird/extensions/inspector@mozilla.org/platform/Linux/chrome/icons/default/winInspectorMain16.xpm
Songbird/extensions/inspector@mozilla.org/platform/WINNT/
Songbird/extensions/inspector@mozilla.org/platform/WINNT/chrome/
Songbird/extensions/inspector@mozilla.org/platform/WINNT/chrome/icons/
Songbird/extensions/inspector@mozilla.org/platform/WINNT/chrome/icons/default/
Songbird/extensions/inspector@mozilla.org/platform/WINNT/chrome/icons/default/winInspectorMain.ico
Songbird/extensions/inspector@mozilla.org/platform/OS2/
Songbird/extensions/inspector@mozilla.org/platform/OS2/chrome/
Songbird/extensions/inspector@mozilla.org/platform/OS2/chrome/icons/
Songbird/extensions/inspector@mozilla.org/platform/OS2/chrome/icons/default/
Songbird/extensions/inspector@mozilla.org/platform/OS2/chrome/icons/default/winInspectorMain.ico
Songbird/extensions/inspector@mozilla.org/components/
Songbird/extensions/inspector@mozilla.org/components/inspector-cmdline.js
Songbird/extensions/inspector@mozilla.org/chrome/
Songbird/extensions/inspector@mozilla.org/chrome/inspector.jar
Songbird/extensions/inspector@mozilla.org/defaults/
Songbird/extensions/inspector@mozilla.org/defaults/preferences/
Songbird/extensions/inspector@mozilla.org/defaults/preferences/inspector.js
Songbird/extensions/inspector@mozilla.org/chrome.manifest
Songbird/extensions/inspector@mozilla.org/install.rdf
Songbird/extensions/basic-layouts@songbirdnest.com/
Songbird/extensions/basic-layouts@songbirdnest.com/install.rdf
Songbird/extensions/rubberducky@songbirdnest.com/
Songbird/extensions/rubberducky@songbirdnest.com/install.rdf
Songbird/LICENSE.txt
Songbird/plugins/
Songbird/README.txt
Songbird/scripts/
Songbird/scripts/sbPlaylistHandlerUtils.js
Songbird/scripts/sbM3UPlaylistHandler.js
Songbird/scripts/sbPLSPlaylistHandler.js
Songbird/scripts/sbFeedPlaylistHandler.js
Songbird/scripts/sbHTMLPlaylistHandler.js
Songbird/scripts/sbASXPlaylistHandler.js
Songbird/searchplugins/
Songbird/searchplugins/hypemachine.xml
Songbird/searchplugins/google-lyrics.xml
Songbird/searchplugins/songbird-internal-search.xml
Songbird/searchplugins/skreemr.xml
Songbird/searchplugins/yahoo-lyrics.xml
Songbird/songbird
Songbird/TRADEMARK.txt
Songbird/xulrunner/
Songbird/xulrunner/bloaturls.txt
Songbird/xulrunner/chrome/
Songbird/xulrunner/chrome/icons/
Songbird/xulrunner/chrome/icons/default/
Songbird/xulrunner/chrome/icons/default/default.xpm
Songbird/xulrunner/chrome/en-US.manifest
Songbird/xulrunner/chrome/en-US.jar
Songbird/xulrunner/chrome/toolkit.jar
Songbird/xulrunner/chrome/comm.manifest
Songbird/xulrunner/chrome/comm.jar
Songbird/xulrunner/chrome/toolkit.manifest
Songbird/xulrunner/chrome/classic.jar
Songbird/xulrunner/chrome/classic.manifest
Songbird/xulrunner/chrome/pippki.manifest
Songbird/xulrunner/chrome/pippki.jar
Songbird/xulrunner/components/
Songbird/xulrunner/components/xpcom_base.xpt
Songbird/xulrunner/components/xpcom_ds.xpt
Songbird/xulrunner/components/xpcom_io.xpt
Songbird/xulrunner/components/xpcom_components.xpt
Songbird/xulrunner/components/xpcom_threads.xpt
Songbird/xulrunner/components/xpcom_xpti.xpt
Songbird/xulrunner/components/proxyObjInst.xpt
Songbird/xulrunner/components/xpcom_system.xpt
Songbird/xulrunner/components/storage.xpt
Songbird/xulrunner/components/pref.xpt
Songbird/xulrunner/components/unicharutil.xpt
Songbird/xulrunner/components/uconv.xpt
Songbird/xulrunner/components/locale.xpt
Songbird/xulrunner/components/intl.xpt
Songbird/xulrunner/components/lwbrk.xpt
Songbird/xulrunner/components/necko.xpt
Songbird/xulrunner/components/nsProxyAutoConfig.js
Songbird/xulrunner/components/nsScriptableIO.js
Songbird/xulrunner/components/necko_cookie.xpt
Songbird/xulrunner/components/necko_dns.xpt
Songbird/xulrunner/components/necko_socket.xpt
Songbird/xulrunner/components/mimetype.xpt
Songbird/xulrunner/components/necko_strconv.xpt
Songbird/xulrunner/components/necko_cache.xpt
Songbird/xulrunner/components/necko_about.xpt
Songbird/xulrunner/components/necko_res.xpt
Songbird/xulrunner/components/necko_file.xpt
Songbird/xulrunner/components/necko_http.xpt
Songbird/xulrunner/components/necko_viewsource.xpt
Songbird/xulrunner/components/necko_ftp.xpt
Songbird/xulrunner/components/xpconnect.xpt
Songbird/xulrunner/components/chardet.xpt
Songbird/xulrunner/components/zipwriter.xpt
Songbird/xulrunner/components/jar.xpt
Songbird/xulrunner/components/cookie.xpt
Songbird/xulrunner/components/rdf.xpt
Songbird/xulrunner/components/jsdservice.xpt
Songbird/xulrunner/components/uriloader.xpt
Songbird/xulrunner/components/exthandler.xpt
Songbird/xulrunner/components/nsHandlerService.js
Songbird/xulrunner/components/nsWebHandlerApp.js
Songbird/xulrunner/components/prefetch.xpt
Songbird/xulrunner/components/caps.xpt
Songbird/xulrunner/components/saxparser.xpt
Songbird/xulrunner/components/htmlparser.xpt
Songbird/xulrunner/components/gfx.xpt
Songbird/xulrunner/components/imglib2.xpt
Songbird/xulrunner/components/plugin.xpt
Songbird/xulrunner/components/dom_base.xpt
Songbird/xulrunner/components/dom_canvas.xpt
Songbird/xulrunner/components/dom_core.xpt
Songbird/xulrunner/components/dom_html.xpt
Songbird/xulrunner/components/dom_events.xpt
Songbird/xulrunner/components/dom_stylesheets.xpt
Songbird/xulrunner/components/dom_views.xpt
Songbird/xulrunner/components/dom_sidebar.xpt
Songbird/xulrunner/components/dom_css.xpt
Songbird/xulrunner/components/dom_traversal.xpt
Songbird/xulrunner/components/dom_range.xpt
Songbird/xulrunner/components/dom_xbl.xpt
Songbird/xulrunner/components/dom_xpath.xpt
Songbird/xulrunner/components/dom_loadsave.xpt
Songbird/xulrunner/components/dom_xul.xpt
Songbird/xulrunner/components/dom_storage.xpt
Songbird/xulrunner/components/dom_offline.xpt
Songbird/xulrunner/components/dom_svg.xpt
Songbird/xulrunner/components/dom.xpt
Songbird/xulrunner/components/widget.xpt
Songbird/xulrunner/components/content_base.xpt
Songbird/xulrunner/components/content_html.xpt
Songbird/xulrunner/components/content_htmldoc.xpt
Songbird/xulrunner/components/content_xmldoc.xpt
Songbird/xulrunner/components/xuldoc.xpt
Songbird/xulrunner/components/xultmpl.xpt
Songbird/xulrunner/components/content_xslt.xpt
Songbird/xulrunner/components/txEXSLTRegExFunctions.js
Songbird/xulrunner/components/content_xtf.xpt
Songbird/xulrunner/components/editor.xpt
Songbird/xulrunner/components/txtsvc.xpt
Songbird/xulrunner/components/txmgr.xpt
Songbird/xulrunner/components/composer.xpt
Songbird/xulrunner/components/layout_base.xpt
Songbird/xulrunner/components/layout_xul.xpt
Songbird/xulrunner/components/layout_xul_tree.xpt
Songbird/xulrunner/components/layout_printing.xpt
Songbird/xulrunner/components/inspector.xpt
Songbird/xulrunner/components/docshell.xpt
Songbird/xulrunner/components/shistory.xpt
Songbird/xulrunner/components/webshell_idls.xpt
Songbird/xulrunner/components/embed_base.xpt
Songbird/xulrunner/components/windowwatcher.xpt
Songbird/xulrunner/components/find.xpt
Songbird/xulrunner/components/webbrowserpersist.xpt
Songbird/xulrunner/components/commandhandler.xpt
Songbird/xulrunner/components/nsHelperAppDlg.js
Songbird/xulrunner/components/nsProgressDialog.js
Songbird/xulrunner/components/webBrowser_core.xpt
Songbird/xulrunner/components/appshell.xpt
Songbird/xulrunner/components/oji.xpt
Songbird/xulrunner/components/accessibility.xpt
Songbird/xulrunner/components/chrome.xpt
Songbird/xulrunner/components/profile.xpt
Songbird/xulrunner/components/mozbrwsr.xpt
Songbird/xulrunner/components/mozfind.xpt
Songbird/xulrunner/components/filepicker.xpt
Songbird/xulrunner/components/nsFilePicker.js
Songbird/xulrunner/components/windowds.xpt
Songbird/xulrunner/components/directory.xpt
Songbird/xulrunner/components/nsResetPref.js
Songbird/xulrunner/components/toolkitremote.xpt
Songbird/xulrunner/components/urlformatter.xpt
Songbird/xulrunner/components/nsURLFormatter.js
Songbird/xulrunner/components/contentprefs.xpt
Songbird/xulrunner/components/nsContentPrefService.js
Songbird/xulrunner/components/jsconsole-clhandler.js
Songbird/xulrunner/components/fastfind.xpt
Songbird/xulrunner/components/alerts.xpt
Songbird/xulrunner/components/feeds.xpt
Songbird/xulrunner/components/FeedProcessor.js
Songbird/xulrunner/components/places.xpt
Songbird/xulrunner/components/nsLivemarkService.js
Songbird/xulrunner/components/nsTaggingService.js
Songbird/xulrunner/components/autocomplete.xpt
Songbird/xulrunner/components/satchel.xpt
Songbird/xulrunner/components/loginmgr.xpt
Songbird/xulrunner/components/nsLoginManager.js
Songbird/xulrunner/components/nsLoginManagerPrompter.js
Songbird/xulrunner/components/nsLoginInfo.js
Songbird/xulrunner/components/storage-Legacy.js
Songbird/xulrunner/components/downloads.xpt
Songbird/xulrunner/components/nsDownloadManagerUI.js
Songbird/xulrunner/components/commandlines.xpt
Songbird/xulrunner/components/appstartup.xpt
Songbird/xulrunner/components/nsTryToClose.js
Songbird/xulrunner/components/nsDefaultCLH.js
Songbird/xulrunner/components/spellchecker.xpt
Songbird/xulrunner/components/toolkitprofile.xpt
Songbird/xulrunner/components/crashreporter.xpt
Songbird/xulrunner/components/xulapp.xpt
Songbird/xulrunner/components/extensions.xpt
Songbird/xulrunner/components/nsExtensionManager.js
Songbird/xulrunner/components/nsBlocklistService.js
Songbird/xulrunner/components/update.xpt
Songbird/xulrunner/components/nsUpdateService.js
Songbird/xulrunner/components/pluginGlue.js
Songbird/xulrunner/components/nsContentDispatchChooser.js
Songbird/xulrunner/components/xpinstall.xpt
Songbird/xulrunner/components/pipboot.xpt
Songbird/xulrunner/components/pipnss.xpt
Songbird/xulrunner/components/pippki.xpt
Songbird/xulrunner/components/autoconfig.xpt
Songbird/xulrunner/components/libimgicon.so
Songbird/xulrunner/components/imgicon.xpt
Songbird/xulrunner/components/xml-rpc.xpt
Songbird/xulrunner/components/nsDictionary.js
Songbird/xulrunner/components/nsXmlRpcClient.js
Songbird/xulrunner/components/xulapp_setup.xpt
Songbird/xulrunner/components/nsXULAppInstall.js
Songbird/xulrunner/crashreporter
Songbird/xulrunner/crashreporter.ini
Songbird/xulrunner/defaults/
Songbird/xulrunner/defaults/autoconfig/
Songbird/xulrunner/defaults/autoconfig/prefcalls.js
Songbird/xulrunner/defaults/autoconfig/platform.js
Songbird/xulrunner/defaults/profile/
Songbird/xulrunner/defaults/profile/chrome/
Songbird/xulrunner/defaults/profile/chrome/userContent-example.css
Songbird/xulrunner/defaults/profile/chrome/userChrome-example.css
Songbird/xulrunner/defaults/profile/US/
Songbird/xulrunner/defaults/profile/US/chrome/
Songbird/xulrunner/defaults/profile/US/chrome/userContent-example.css
Songbird/xulrunner/defaults/profile/US/chrome/userChrome-example.css
Songbird/xulrunner/defaults/profile/US/localstore.rdf
Songbird/xulrunner/defaults/profile/localstore.rdf
Songbird/xulrunner/defaults/pref/
Songbird/xulrunner/defaults/pref/xulrunner.js
Songbird/xulrunner/dependentlibs.list
Songbird/xulrunner/dictionaries/
Songbird/xulrunner/dictionaries/en-US.dic
Songbird/xulrunner/dictionaries/en-US.aff
Songbird/xulrunner/updater.ini
Songbird/xulrunner/greprefs/
Songbird/xulrunner/greprefs/all.js
Songbird/xulrunner/greprefs/security-prefs.js
Songbird/xulrunner/greprefs/xpinstall.js
Songbird/xulrunner/icons/
Songbird/xulrunner/icons/mozicon50.xpm
Songbird/xulrunner/icons/mozicon16.xpm
Songbird/xulrunner/icons/document.png
Songbird/xulrunner/libfreebl3.chk
Songbird/xulrunner/libfreebl3.so
Songbird/xulrunner/libmozjs.so
Songbird/xulrunner/libnspr4.so
Songbird/xulrunner/libnss3.so
Songbird/xulrunner/libnssckbi.so
Songbird/xulrunner/libnssdbm3.so
Songbird/xulrunner/libplc4.so
Songbird/xulrunner/libplds4.so
Songbird/xulrunner/libsmime3.so
Songbird/xulrunner/libsoftokn3.chk
Songbird/xulrunner/libsoftokn3.so
Songbird/xulrunner/libsqlite3.so
Songbird/xulrunner/libssl3.so
Songbird/xulrunner/libxpcom.so
Songbird/xulrunner/libxul.so
Songbird/xulrunner/LICENSE
Songbird/xulrunner/mangle
Songbird/xulrunner/modules/
Songbird/xulrunner/modules/XPCOMUtils.jsm
Songbird/xulrunner/modules/JSON.jsm
Songbird/xulrunner/modules/ISO8601DateUtils.jsm
Songbird/xulrunner/modules/Microformats.js
Songbird/xulrunner/mozilla-xremote-client
Songbird/xulrunner/nsinstall
Songbird/xulrunner/platform.ini
Songbird/xulrunner/plugins/
Songbird/xulrunner/plugins/libunixprintplugin.so
Songbird/xulrunner/plugins/libnullplugin.so
Songbird/xulrunner/README.txt
Songbird/xulrunner/regxpcom
Songbird/xulrunner/res/
Songbird/xulrunner/res/bloatcycle.html
Songbird/xulrunner/res/entityTables/
Songbird/xulrunner/res/entityTables/htmlEntityVersions.properties
Songbird/xulrunner/res/entityTables/html40Latin1.properties
Songbird/xulrunner/res/entityTables/html40Symbols.properties
Songbird/xulrunner/res/entityTables/html40Special.properties
Songbird/xulrunner/res/entityTables/transliterate.properties
Songbird/xulrunner/res/entityTables/mathml20.properties
Songbird/xulrunner/res/charsetalias.properties
Songbird/xulrunner/res/charsetData.properties
Songbird/xulrunner/res/unixcharset.properties
Songbird/xulrunner/res/langGroups.properties
Songbird/xulrunner/res/language.properties
Songbird/xulrunner/res/effective_tld_names.dat
Songbird/xulrunner/res/hiddenWindow.html
Songbird/xulrunner/res/dtd/
Songbird/xulrunner/res/dtd/xhtml11.dtd
Songbird/xulrunner/res/dtd/mathml.dtd
Songbird/xulrunner/res/EditorOverride.css
Songbird/xulrunner/res/grabber.gif
Songbird/xulrunner/res/table-add-column-after-active.gif
Songbird/xulrunner/res/table-add-column-after-hover.gif
Songbird/xulrunner/res/table-add-column-after.gif
Songbird/xulrunner/res/table-add-column-before-active.gif
Songbird/xulrunner/res/table-add-column-before-hover.gif
Songbird/xulrunner/res/table-add-column-before.gif
Songbird/xulrunner/res/table-add-row-after-active.gif
Songbird/xulrunner/res/table-add-row-after-hover.gif
Songbird/xulrunner/res/table-add-row-after.gif
Songbird/xulrunner/res/table-add-row-before-active.gif
Songbird/xulrunner/res/table-add-row-before-hover.gif
Songbird/xulrunner/res/table-add-row-before.gif
Songbird/xulrunner/res/table-remove-column-active.gif
Songbird/xulrunner/res/table-remove-column-hover.gif
Songbird/xulrunner/res/table-remove-column.gif
Songbird/xulrunner/res/table-remove-row-active.gif
Songbird/xulrunner/res/table-remove-row-hover.gif
Songbird/xulrunner/res/table-remove-row.gif
Songbird/xulrunner/res/forms.css
Songbird/xulrunner/res/ua.css
Songbird/xulrunner/res/html.css
Songbird/xulrunner/res/quirk.css
Songbird/xulrunner/res/viewsource.css
Songbird/xulrunner/res/arrow.gif
Songbird/xulrunner/res/arrowd.gif
Songbird/xulrunner/res/contenteditable.css
Songbird/xulrunner/res/designmode.css
Songbird/xulrunner/res/html/
Songbird/xulrunner/res/html/folder.png
Songbird/xulrunner/res/broken-image.gif
Songbird/xulrunner/res/loading-image.gif
Songbird/xulrunner/res/mathml.css
Songbird/xulrunner/res/fonts/
Songbird/xulrunner/res/fonts/mathfont.properties
Songbird/xulrunner/res/fonts/mathfontUnicode.properties
Songbird/xulrunner/res/fonts/mathfontSTIXNonUnicode.properties
Songbird/xulrunner/res/fonts/mathfontSTIXSize1.properties
Songbird/xulrunner/res/fonts/mathfontStandardSymbolsL.properties
Songbird/xulrunner/res/svg.css
Songbird/xulrunner/res/cmessage.txt
Songbird/xulrunner/run-mozilla.sh
Songbird/xulrunner/shlibsign
Songbird/xulrunner/updater
Songbird/xulrunner/xpcshell
Songbird/xulrunner/xpicleanup
Songbird/xulrunner/xpidl
Songbird/xulrunner/xpt_dump
Songbird/xulrunner/xpt_link
Songbird/xulrunner/xulrunner
Songbird/xulrunner/xulrunner-bin
/usr/share/themes/Blubuntu/gtk-2.0/gtkrc:169: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
cannot move `Songbird' to `/usr/local/bin/songbird': No such file or directory
/usr/share/themes/Blubuntu/gtk-2.0/gtkrc:169: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
/usr/share/themes/Blubuntu/gtk-2.0/gtkrc:169: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
/usr/share/themes/Blubuntu/gtk-2.0/gtkrc:169: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
/usr/share/themes/Blubuntu/gtk-2.0/gtkrc:169: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
/usr/share/themes/Blubuntu/gtk-2.0/gtkrc:169: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
/usr/share/themes/Blubuntu/gtk-2.0/gtkrc:169: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
rasmus@rasmus-laptop:~$ 


---

### Post by Martje_001 on 2008-02-26
I don't know why it went wrong on your box, because mine works fine. Here's a deb:

[http://www.getdeb.net/download/1894/0](http://www.getdeb.net/download/1894/0)

---

### Post by rasmusbp on 2008-02-26
thanks a lot, that deb worked fine (except for some chrome registration errors, but I'll probably figure that out!) 

:)

---

### Post by Martje_001 on 2008-02-26
> **rasmusbp said:**
> thanks a lot, that deb worked fine (except for some chrome registration errors, but I'll probably figure that out!) 

:)
Always happy to help :D.

Those chrome registration errors are known bugs.

Cheers!

---

### Post by jeyaganesh on 2008-04-25
Hi Songbird 0.5 released. Please post new script and installation guide to install it. Thanks in advance!

---

### Post by Martje_001 on 2008-04-25
> **jeyaganesh said:**
> Hi Songbird 0.5 released. Please post new script and installation guide to install it. Thanks in advance!
Get the deb-package here:
[http://getdeb.net/app/Songbird](http://getdeb.net/app/Songbird)

---

### Post by jeyaganesh on 2008-04-25
Hello Martje, thanks for your quick reply and the wonderful website. That website is very useful. Thank you very much.

---

### Post by vorostatz on 2008-12-04
Hi all I really loathe songbird and want to remove all traces of it from my Laptop (2.16 Ghz core two duo 1 gig ram).  I cannot find it in either Synaptics package manager or Add/Remove.  I have seen mention here and there of a removal script that seems to work,does anyone know where I can get this script and how to use it, I am kind of a newbie so please T Y P E slow ):P

Many thanks in Advance

---

### Post by Dale61 on 2008-12-04
I've just upgraded to 1.0, but until it has an inbuilt equaliser, I'll still use Amarok as my mp3 player of choice.

---

### Post by magmon on 2008-12-04
Worked perfectly, thanks! Had been trying to get it installed for like 3 days xD.

---

### Post by mrphd on 2008-12-11
> **vorostatz said:**
> Hi all I really loathe songbird and want to remove all traces of it from my Laptop (2.16 Ghz core two duo 1 gig ram).  I cannot find it in either Synaptics package manager or Add/Remove.  I have seen mention here and there of a removal script that seems to work,does anyone know where I can get this script and how to use it, I am kind of a newbie so please T Y P E slow ):P

Many thanks in Advance

how did you install it? did you follow a set of instructions?

---

### Post by vorostatz on 2008-12-15
> **mrphd said:**
> how did you install it? did you follow a set of instructions?

I found an installation script which I used and then like a numbeskull deleted.  So I:

Downloaded the program from songbird site

Copied the installation script I found on this site

Named it a installsongbird.sh

Copied the install script intoterminal

and ran it

Now I want to get rid of songbird, and I have heard there is a removesongbird.sh script I was hoping someone here might know where I can find it

Many thanks in Advance

---

### Post by mrphd on 2008-12-17
Do you mean this: [http://www.psychocats.net/ubuntu/removesongbird.sh](http://www.psychocats.net/ubuntu/removesongbird.sh)

If so, download and then make the script executable

chmod +x removesongbird.sh

and then run it:

./removesongbird.sh

that is all.

---

### Post by vorostatz on 2008-12-20
> **mrphd said:**
> Do you mean this: [http://www.psychocats.net/ubuntu/removesongbird.sh](http://www.psychocats.net/ubuntu/removesongbird.sh)

If so, download and then make the script executable

chmod +x removesongbird.sh

and then run it:

./removesongbird.sh

that is all.

Thank you ...you rock!!!

---

