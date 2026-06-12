---
title: "Is Konqueror really slow, or is it just my installation?"
date: 2010-03-11
forum: The Cafe
---

### Post by swoll1980 on 2010-03-11
On my machine Konqueror runs really slow. I don't have this problem with Firefox. I don't know if it's just my setup, or if it's like this for everyone. What's you experience with it?

---

### Post by themarker0 on 2010-03-11
When i ran mandriva spring 08, i had no issues with it. If anything it was faster then firefox at the time. Are you using a KDE base? I did have troubles with it in general when i moved bases.

---

### Post by The Toxic Mite on 2010-03-11
Likely to just be your config.
 
I've dabbled in and out of Kubuntu a few times, and Konqueror is pretty good, but IMHO it's not as good as Firefox :-/

---

### Post by kellemes on 2010-03-11
Konqueror 4.4.1 is much faster then Firefox 3.6.2pre on my machine..
and so I use Chrome 5.0.307.11 beta ;-)

---

### Post by swoll1980 on 2010-03-11
Huh, now I have to figure out what's wrong with it.

---

### Post by kellemes on 2010-03-11
> **swoll1980 said:**
> Huh, now I have to figure out what's wrong with it.

Run it from terminal and watch the output?

---

### Post by swoll1980 on 2010-03-11
```
konqueror(3789)/kdecore (KSycoca) KSycocaPrivate::openDatabase: Trying to open ksycoca from  "/var/tmp/kdecache-nolan/ksycoca4"
konqueror(3789)/kparts KParts::Plugin::pluginInfos: found KParts Plugin :  "/usr/share/kde4/apps/konqueror/kpartplugins/searchbar.rc"
konqueror(3789)/kparts KParts::Plugin::loadPlugins: load plugin  "searchbar"
konqueror(3789)/kurifilter (plugins) KURISearchFilterEngine::loadConfig: ( 3789 )  Keywords Engine: Loading config...
konqueror(3789)/kurifilter (plugins) KURISearchFilterEngine::loadConfig: ( 3789 )  Keyword Delimiter:  :
konqueror(3789)/kurifilter (plugins) KURISearchFilterEngine::loadConfig: ( 3789 )  Default Search Engine:  "google_kubuntu"
konqueror(3789)/kurifilter (plugins) KURISearchFilterEngine::loadConfig: ( 3789 )  Web Shortcuts Enabled:  true
konqueror(3789)/kurifilter (plugins) KURISearchFilterEngine::loadConfig: ( 3789 )  Verbose:  false
konqueror(3789)/kurifilter (plugins) KURISearchFilterEngine::formatResult: ( 3789 )  user query  = ' "some keyword" '
konqueror(3789)/kurifilter (plugins) KURISearchFilterEngine::formatResult: ( 3789 )  query definition  = ' "http://www.google.com/search?q=\{@}&ie=UTF-8&oe=UTF-8" '
konqueror(3789)/kurifilter (plugins) KURISearchFilterEngine::modifySubstitutionMap: ( 3789 )  Generating substitution map:
konqueror(3789)/kurifilter (plugins) KURISearchFilterEngine::modifySubstitutionMap: ( 3789 )  "  map['0']"  = ' "some keyword" '
konqueror(3789)/kurifilter (plugins) KURISearchFilterEngine::modifySubstitutionMap: ( 3789 )  "  map['1']"  = ' "some" '
konqueror(3789)/kurifilter (plugins) KURISearchFilterEngine::modifySubstitutionMap: ( 3789 )  "  map['2']"  = ' "keyword" '
konqueror(3789)/kurifilter (plugins) KURISearchFilterEngine::substituteQuery: ( 3789 )  Substitute references:
konqueror(3789)/kurifilter (plugins) KURISearchFilterEngine::substituteQuery: ( 3789 )    reference list  = ' "@" '
konqueror(3789)/kurifilter (plugins) KURISearchFilterEngine::substituteQuery: ( 3789 )    newurl  = ' "http://www.google.com/search?q=\@&ie=UTF-8&oe=UTF-8" '
konqueror(3789)/kurifilter (plugins) KURISearchFilterEngine::substituteQuery: ( 3789 )      rest  = ' "some keyword" '
konqueror(3789)/kurifilter (plugins) KURISearchFilterEngine::formatResult: ( 3789 )  substituted query  = ' "http://www.google.com/search?q=some+keyword&ie=UTF-8&oe=UTF-8" '
konqueror(3789)/kparts KParts::Plugin::pluginInfos: found KParts Plugin :  "/usr/share/kde4/apps/khtml/kpartplugins/khtmlkttsd.rc"
konqueror(3789)/kparts KParts::Plugin::loadPlugins: load plugin  "khtmlkttsdplugin"
konqueror(3789)/kio (KIOConnection) KIO::ConnectionServer::listenForRemote: Listening on  "local:/tmp/ksocket-nolan/konquerorrA3789.slave-socket"
konqueror(3789)/kio (Slave) KIO::Slave::createSlave: createSlave "file" for KUrl("file:///usr/share/kde4/apps/kdeui/about/kde_infopage.css")
konqueror(3789)/kio (KIOConnection) KIO::ConnectionServer::listenForRemote: Listening on  "local:/tmp/ksocket-nolan/konquerorWl3789.slave-socket"
konqueror(3789)/kio (Slave) KIO::Slave::createSlave: createSlave "file" for KUrl("file:///usr/share/kde4/apps/konqueror/about/konq.css")
konqueror(3789)/kio (KIOConnection) KIO::ConnectionServer::listenForRemote: Listening on  "local:/tmp/ksocket-nolan/konquerorxL3789.slave-socket"
konqueror(3789)/kio (Slave) KIO::Slave::createSlave: createSlave "file" for KUrl("file:///usr/share/icons/oxygen/48x48/places/bookmarks.png")
konqueror(3789)/kio (KIOConnection) KIO::ConnectionServer::listenForRemote: Listening on  "local:/tmp/ksocket-nolan/konquerorVr3789.slave-socket"
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /home/nolan/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 
konqueror(3789)/kio (Slave) KIO::Slave::createSlave: createSlave "file" for KUrl("file:///usr/share/kde4/apps/kdeui/about/box-top-right.png")
konqueror(3789)/kio (KIOConnection) KIO::ConnectionServer::listenForRemote: Listening on  "local:/tmp/ksocket-nolan/konquerorcH3789.slave-socket"
konqueror(3789)/kio (Slave) KIO::Slave::createSlave: createSlave "file" for KUrl("file:///usr/share/kde4/apps/kdeui/about/box-top-middle.png")
konqueror(3789)/kio (KIOConnection) KIO::ConnectionServer::listenForRemote: Listening on  "local:/tmp/ksocket-nolan/konquerorNb3789.slave-socket"
konqueror(3789)/kio (Slave) KIO::Slave::createSlave: createSlave "file" for KUrl("file:///usr/share/kde4/apps/kdeui/about/box-middle-left.png")
konqueror(3789)/kio (KIOConnection) KIO::ConnectionServer::listenForRemote: Listening on  "local:/tmp/ksocket-nolan/konquerorfo3789.slave-socket"
konqueror(3789)/kio (Slave) KIO::Slave::createSlave: createSlave "file" for KUrl("file:///usr/share/kde4/apps/kdeui/about/box-center.png")
konqueror(3789)/kio (KIOConnection) KIO::ConnectionServer::listenForRemote: Listening on  "local:/tmp/ksocket-nolan/konqueroruI3789.slave-socket"
konqueror(3789)/kio (Slave) KIO::Slave::createSlave: createSlave "file" for KUrl("file:///usr/share/kde4/apps/kdeui/about/box-middle-right.png")
konqueror(3789)/kio (KIOConnection) KIO::ConnectionServer::listenForRemote: Listening on  "local:/tmp/ksocket-nolan/konquerorVd3789.slave-socket"
konqueror(3789)/kio (Slave) KIO::Slave::createSlave: createSlave "file" for KUrl("file:///usr/share/kde4/apps/kdeui/about/box-bottom-left.png")
konqueror(3789)/kio (KIOConnection) KIO::ConnectionServer::listenForRemote: Listening on  "local:/tmp/ksocket-nolan/konquerorzU3789.slave-socket"
konqueror(3789)/kio (Slave) KIO::Slave::createSlave: createSlave "file" for KUrl("file:///usr/share/kde4/apps/kdeui/about/box-bottom-right.png")
konqueror(3789)/kio (KIOConnection) KIO::ConnectionServer::listenForRemote: Listening on  "local:/tmp/ksocket-nolan/konquerorEG3789.slave-socket"
konqueror(3789)/kio (Slave) KIO::Slave::createSlave: createSlave "file" for KUrl("file:///usr/share/kde4/apps/kdeui/about/box-bottom-middle.png")
konqueror(3789)/kio (KIOConnection) KIO::ConnectionServer::listenForRemote: Listening on  "local:/tmp/ksocket-nolan/konqueroreJ3789.slave-socket"
konqueror(3789)/kio (bookmarks) KonqBookmarkMenu::actionForBookmark: Creating Konq bookmark action named  "Ubuntu Forums"
konqueror(3789)/kio (bookmarks) KonqBookmarkMenu::actionForBookmark: Creating Konq bookmark action named  "The Community Cafe - Ubuntu Forums"
konqueror(3789)/kdecore (KSycoca) KSycocaPrivate::openDatabase: Trying to open ksycoca from  "/var/tmp/kdecache-nolan/ksycoca4"
konqueror(3789)/kdecore (KNetwork resolver) <unnamed>::ResInitUsage::shouldResInit: shouldResInit: /etc/resolv.conf updated
konqueror(3789)/kparts KParts::BrowserRun::scanFile: KUrl("http://ubuntuforums.org/forumdisplay.php?f=11")
konqueror(3789)/kio (Slave) KIO::Slave::createSlave: createSlave "http" for KUrl("http://ubuntuforums.org/forumdisplay.php?f=11")
konqueror(3789)/kio (KIOConnection) KIO::ConnectionServer::listenForRemote: Listening on  "local:/tmp/ksocket-nolan/konqueroryV3789.slave-socket"
konqueror(3789)/kparts KParts::BrowserRun::slotBrowserMimetype: found "text/html" for KUrl("http://ubuntuforums.org/forumdisplay.php?f=11")
konqueror(3789)/kdecore (trader) KMimeTypeTrader::query: query for mimeType  "text/html" ,  "Application"  : returning  7  offers
konqueror(3789)/kdecore (trader) KMimeTypeTrader::query: query for mimeType  "text/html" ,  "KParts/ReadOnlyPart"  : returning  2  offers
konqueror(3789)/kdecore (KLibrary) findLibraryInternal: plugins should not have a 'lib' prefix: "libkhtmlpart.so"
konqueror(3789)/kdecore (KLibrary) findLibraryInternal: plugins should not have a 'lib' prefix: "libkhtmlpart.so"
konqueror(3789)/kdecore (KLibrary) kde4Factory: The library "/usr/lib/kde4/libkhtmlpart.so" does not offer a qt_plugin_instance function.
konqueror(3789)/khtml KHTMLFactory::KHTMLFactory: KHTMLFactory(0x13220c0)
konqueror(3789)/kparts KParts::Plugin::pluginInfos: found KParts Plugin :  "/usr/share/kde4/apps/khtml/kpartplugins/khtmlkttsd.rc"
konqueror(3789)/kparts KParts::Plugin::loadPlugins: load plugin  "khtmlkttsdplugin"
konqueror(3789)/khtml (part) KHTMLPart::~KHTMLPart: KHTMLPart(0xc49a10)
konqueror(3789)/kparts KParts::Part::~Part: deleting widget QWidget(0xcc6cb0, name = "khtml_part_widget") "khtml_part_widget"
konqueror(3789)/khtml (part) KHTMLPart::openUrl: KHTMLPart(0xe2d040) opening KUrl("http://ubuntuforums.org/forumdisplay.php?f=11")
konqueror(3789)/kio (bookmarks) KBookmark::updateAccessMetadata: KBookmark::updateAccessMetadata  "/1"   "http://ubuntuforums.org/forumdisplay.php?f=11"
konqueror(3789)/kio (bookmarks) KBookmarkManager::saveAs: KBookmarkManager::save  "/home/nolan/.kde/share/apps/konqueror/bookmarks.xml"
konqueror(3789)/kio (Scheduler) KIO::SchedulerPrivate::findIdleSlave: Resume metadata is ""
konqueror(3789)/kio (Scheduler) KIO::SchedulerPrivate::findIdleSlave: HOLD: Reusing held slave for KUrl("http://ubuntuforums.org/forumdisplay.php?f=11")
konqueror(3789)/khtml (html) DOM::HTMLDocumentImpl::changeModes:  using compatibility parseMode
konqueror(3789)/khtml (html) DOM::HTMLDocumentImpl::changeModes:  using transitional parseMode
konqueror(3789)/kio (Slave) KIO::Slave::createSlave: createSlave "http" for KUrl("http://ubuntuforums.org/clientscript/vbulletin_css/style-e9e10bd9-00098.css")
konqueror(3789)/kio (KIOConnection) KIO::ConnectionServer::listenForRemote: Listening on  "local:/tmp/ksocket-nolan/konquerorIA3789.slave-socket"
konqueror(3789)/kio (Slave) KIO::Slave::createSlave: createSlave "http" for KUrl("http://yui.yahooapis.com/2.7.0/build/yahoo-dom-event/yahoo-dom-event.js?v=384")
konqueror(3789)/kio (KIOConnection) KIO::ConnectionServer::listenForRemote: Listening on  "local:/tmp/ksocket-nolan/konquerorNi3789.slave-socket"
konqueror(3789)/kio (Slave) KIO::Slave::createSlave: createSlave "http" for KUrl("http://ubuntuforums.org/clientscript/vbulletin_important.css?v=384")
konqueror(3789)/kio (KIOConnection) KIO::ConnectionServer::listenForRemote: Listening on  "local:/tmp/ksocket-nolan/konquerorvc3789.slave-socket"
konqueror(3789)/khtml (tokenizer) khtml::HTMLTokenizer::notifyFinished: Finished loading an external script
konqueror(3789)/khtml (tokenizer) khtml::HTMLTokenizer::notifyFinished: Finished loading an external script
konqueror(3789)/khtml (tokenizer) khtml::HTMLTokenizer::notifyFinished: Finished loading an external script
konqueror(3789)/khtml (tokenizer) khtml::HTMLTokenizer::notifyFinished: Finished loading an external script
konqueror(3789)/kio (Slave) KIO::Slave::createSlave: createSlave "http" for KUrl("http://ubuntuforums.org/images/misc/navbits_finallink_ltr.gif")
konqueror(3789)/kio (KIOConnection) KIO::ConnectionServer::listenForRemote: Listening on  "local:/tmp/ksocket-nolan/konquerorqH3789.slave-socket"
konqueror(3789)/kio (Slave) KIO::Slave::createSlave: createSlave "http" for KUrl("http://ubuntuforums.org/images/misc/menu_open.gif")
konqueror(3789)/kio (KIOConnection) KIO::ConnectionServer::listenForRemote: Listening on  "local:/tmp/ksocket-nolan/konquerorme3789.slave-socket"
konqueror(3789)/khtml (tokenizer) khtml::HTMLTokenizer::notifyFinished: Finished loading an external script
konqueror(3789)/khtml (tokenizer) khtml::HTMLTokenizer::notifyFinished: Finished loading an external script
konqueror(3789)/kio (bookmarks) KBookmark::updateAccessMetadata: KBookmark::updateAccessMetadata  "/1"   "http://ubuntuforums.org/forumdisplay.php?f=11"
konqueror(3789)/kio (bookmarks) KBookmarkManager::saveAs: KBookmarkManager::save  "/home/nolan/.kde/share/apps/konqueror/bookmarks.xml"
konqueror(3789)/khtml (caret) DOM::Selection::moveTo: Selection[ Position( 0x0 "null" : 0 ) Position( 0x0 "null" : 0 ) Position( 0x0 "null" : 0 ) Position( 0x0 "null" : 0 ) 1 ] Position( 0x0 "null" : 0 ) Position( 0x0 "null" : 0 )
konqueror(3789)/khtml (caret) DOM::Selection::validate: Selection[ Position( 0x0 "null" : 0 ) Position( 0x0 "null" : 0 ) Position( 0x0 "null" : 0 ) Position( 0x0 "null" : 0 ) 1 ] 0
konqueror(3789)/khtml (caret) DOM::Selection::validate: [character:baseIsStart] true Position( 0x0 "null" : 0 ) Position( 0x0 "null" : 0 )
  
```

Might as well be German

---

### Post by kellemes on 2010-03-11
> **swoll1980 said:**
> 
Might as well be German

No it isn't.. it's another language.
I don't understand.

---

### Post by sandyd on 2010-03-11
same here. slow as a turtle.

---

### Post by kellemes on 2010-03-11
What version are we talking about anyway?
With KDE4 keeping up to date really pays these day.. every release is getting better and faster.

---

### Post by swoll1980 on 2010-03-11
> **kellemes said:**
> What version are we talking about anyway?
With KDE4 keeping up to date really pays these day.. every release is getting better and faster.

I'm using 4.4.1 I believe. I had this problem in 4.3 as well though.

---

### Post by Name change on 2010-03-11
My Konqueror can be fast and it can be pinstakingly slow...
it's slow mostly on Wikipedia and some other wikis, and sometimes it just grinds to a halt for no real reason...
I still prefer it any other browser; I'm special that way.

---

