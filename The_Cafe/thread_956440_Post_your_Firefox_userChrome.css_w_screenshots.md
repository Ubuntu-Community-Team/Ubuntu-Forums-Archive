---
title: "Post your Firefox userChrome.css w/ screenshots"
date: 2008-10-23
forum: The Cafe
---

### Post by steveydoteu on 2008-10-23
I have been playing around a little with it the past couple of days, would be interested to see its full potential, get some new ideas and such.

Thought it would be good to share knowledge on the matter, see what we all come up with, offer tips and so on.

**Please remember to either attach the files, or post the CSS in code tags!!**

---

### Post by blacksm1th on 2009-04-01
[[IMG]http://img24.imageshack.us/img24/5526/screenshotpostyourfiref.th.png[/IMG]](http://img24.imageshack.us/my.php?image=screenshotpostyourfiref.png)

```
@namespace url("http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul");

/*   ======================================================BEGIN======================================================   */  

/* Hide urlbar and searchbar drop-down arrows */
	#urlbar .autocomplete-history-dropmarker
	  	{ display: none !important; } 
		
	#searchbar .autocomplete-history-dropmarker 
	   	{ display: none !important; }

/* Hide gnome focus border around searchbar */
 	.searchbar-textbox 
		{ -moz-appearance:none!important; }

/* Ubuntu fix */ 
	#searchbar, #urlbar
		{ min-height: 28px !important;
        	max-height: 28px !important; }  

/* Remove search engines button from searchbar*/
       .searchbar-dropmarker#searchbar-dropmarker  
	        { display: none !important; }
       .searchbar-engine-button-container  
	        { display: none !important; }
       .searchbar-engine-button  
		{ display: none !important; } 

/*  Hide Search Engine Name in searchbar  */ 
        textbox[empty="true"] .textbox-input-box 
        	{ color: #323232 !important; } 

/*  Urlbar text left margin  */
        #urlbar .textbox-input-box  
		{ margin-left: 3px !important; }
		
/*  Searchbar text left margin  */
        #searchbar .textbox-input-box 
		{ margin-left: 3px !important; } 		
		
/*  Old style go button without star  */  
        #star-button  
		{ display: none !important; } 
        #go-button  
		{ visibility: visible !important; }

/*  Hide RSS icon from location bar  */        
        #feed-button 
		{ display: none !important }

/* Group reload and stop buttons (user must place stop button before reload on toolbar)*/
        #stop-button[disabled="true"]
		{ display:none; } 
        #stop-button:not([disabled]) + #reload-button 
		{ display:none; }	

/*  Hide Forward Back Dropmaker  */      
        #back-forward-dropmarker 
        	{ display:none; } 		
		
		
		
/*   =================================================================================================================   */            
 
 

/*  Remove Items In Context Menu   */ 
        #context-back, /* "Back" */
	#context-forward, /* "Forward" */
	#context-reload, /* "Reload" */
        #context-stop, /* "Stop" */
	#context-bookmarkpage, /* "Bookmark This Page..." */
	#context-savepage, /* "Save Page As..." */
	#context-sendpage, /* "Send Link..." (showed on webpage) */
	#context-viewbgimage, /* "View Background Image" */

/*  Remove Items In Context Menu: LINKS  */
	#context-bookmarklink, /* "Bookmark This Link..." */
	#context-sendlink, /* "Send Link..." (showed on links) */

/*  Remove Items In Context Menu: IMAGES  */
	#context-viewimage, /* "View Image" */
	#context-copyimage-contents, /* "Copy Image" */
	#context-back, /* "Back" */
	#context-forward, /* "Forward" */
	#context-reload, /* "Reload" */
	#context-stop, /* "Stop" */
	#context-bookmarkpage, /* "Bookmark This Page..." */
	#context-savepage, /* "Save Page As..." */
	#context-sendpage, /* "Send Link..." (showed on webpage) */
	#context-viewbgimage, /* "View Background Image" */
	#context-copyimage, /* "Copy Image Location" */
	#context-sendimage, /* "Send Image..." */
	#context-setWallpaper, /* "Set As Wallpaper..." */
	#context-setDesktopBackground, /* "Set As Desktop Background..." */

/*  Remove Items In Context Menu: LINKS  */
		/*  #context-openlinkintab, /* "Open Link in New Tab" */
	#context-bookmarklink, /* "Bookmark This Link..." */
	#context-sendlink, /* "Send Link..." (showed on links) */
	#context-copyemail, /* "Copy Email Address" */

/*  Remove Items In Context Menu: TEXT  */
        #context-selectall, /* "Select All" */
	#context-viewpartialsource-selection, /* "View Selection Source" */

/*  Remove Items In Context Menu: EXTRA  */
	#context-printpage, /* "Print..." */
	#frame, /* "This Frame" */
	#context-viewsource, /* "View Page Source" */
	#context-viewinfo, /* "View Page Info" */
	#context-metadata, /* "Properties" */
	#context-keywordfield, /* "Add a Keyword for this Search" */
	#formfillerDebugPanel, /* "formfiller statusbar debug of debug" */

		
		
/*   =================================================================================================================   */  	  



/*  File  */
	menuitem[command="cmd_newNavigatorTab"],  /* New Window */
	menuitem[command="Browser:OpenLocation"],  /* Open Location */
	#menu_closeWindow,  /*  */
        #menu_close,  /*  */
        #menu_sendLink,  /*  */
        #goOfflineMenuitem,  /*  */
        menuitem[command="cmd_pageSetup"],  /* Page Setup... */
        menuitem[command="cmd_printPreview"],  /* Print Preview */
        menuitem[command="cmd_print"],  /* Print... */
        menuitem[oncommand^="BrowserImport();"],  /* Import... */
        menuitem[command="cmd_quitApplication"],  /* Quit */
        
/*  Edit  */
	/*	#edit-menu, */
        menuitem[command="cmd_undo"],  /* Undo */
        menuitem[command="cmd_redo"],  /* Redo */
        menuitem[command="cmd_cut"],  /* Cut */
        /*  menuitem[command="cmd_copy"],     Copy */
        /*  menuitem[command="cmd_paste"],     Paste */ 
        /*  menuitem[command="cmd_delete"],     Delete */
        menuitem[command="cmd_selectAll"],  /* Select All */
        menuitem[command="cmd_find"],  /* Find */
        menuitem[command="cmd_findAgain"],  /* Find Again */

/*  View  */
	#viewToolbarsMenu,  /* Toolbars */
	menuitem[command="Browser:Stop"],  /* Stop */
	menuitem[command="Browser:Reload"],  /* Reload */
        menuitem[command="View:FullScreen"],  /* Full Screen */
        
/*  History  */
	menuitem[oncommand^="BrowserBack(event, true)"],  /* Back */
	menuitem[oncommand^="BrowserForward(event, true)"],  /* Forward */
	menuitem[oncommand^="BrowserGoHome(event);"],  /* Home */
        #historyUndoMenu,  /* Recently Closed Tabs */

/* Bookmarks  */
	menuitem[command="Browser:AddBookmarkAs"],  /*  */
	menuitem[command="Browser:BookmarkAllTabs"],  /*  */
	menuitem[label="Get Bookmark Add-ons"],  /*  */
	#subscribeToPageMenuitem,  /*  */
        #bookmarksToolbarFolderMenu,   /*  */

/*  Tools  */
	menuitem[command="Tools:Search"],  /*  */
	#tabmix-menu,   /*  */
        #tm-sm-closedwindows,   /*  */
       /* #tm-sm-settings,     */
        #tm-sm-closedwindows2,   /*  */
        #tm-sm-saveone,   /*  */
        #tm-sm-saveall,   /*  */
        #flashgot-menu,  /*  */
        #abp-menuitem,   /*  */
        
/*  Help  */
       /* menuitem[oncommand^="openHelpLink('ieusers');"],   For Internet Explorer Users */
	#menu_HelpPopup_reportertoolmenu,  /*  */
	#menu_HelpPopup_reportPhishingtoolmenu,  /*  */
        menuitem[oncommand^="openReleaseNotes(event)"],  /* Release Notes */
        menuitem[oncommand^="openHelpLink('firefox-help')"]    /* Help Contents */
               { display: none !important; }
      
	  
	  
/*   ========================================================TABS=====================================================   */  


	   
/*  First tab left margin  */
        .tabbrowser-tab[first-tab="true"]
        	{ margin-left: 1px !important; } 

/*  Show first tab without padding on the left  */  
        .tabs-container:not([overflow="true"]) 
        	{ -moz-padding-start: 0px !important; }

/*  Distance between all tabs  */
        .tabbrowser-tabs .tabbrowser-tab 
        	{ margin-right: 1px !important; }
		
/*  Hide focus rings around active tab  */
        .tabbrowser-tabs > tab:focus .tab-middle
        	{-moz-outline: none !important; }  
        .tab-text
        	{ border: none !important; }   
        .tabbrowser-tab[selected="true"]:focus
        	{ -moz-border-top-colors: #000000 #DFE2E6 #D0D7DD !important;
        	-moz-border-right-colors: #000000 #BAC2CD #C1C9D3 !important;
        	-moz-border-bottom-colors: #C7D0D9 !important;
        	-moz-border-left-colors: #000000 #DFE2E6 #D0D7DD !important; }
        
/*  Static throbber on Bars  */
	#navigator-throbber 
		{ list-style-image: url("throbber-16.gif") !important; }

/*  Animated throbber on Bars  */
	#navigator-throbber[busy="true"] 
		{ list-style-image: url("throbber-16-anim.gif") !important; }

/*  Animated throbber on Tabs  */
	#main-window[firefox3] .tabbrowser-tab[busy]
		 > hbox.tab-image-middle > .tab-icon > .tab-icon-image
		{ list-style-image: url("throbber-16-anim.gif") !important;
		opacity: 1.0 !important; }

	#main-window[firefox3] .alltabs-item[busy] > .menu-iconic-left > .menu-iconic-icon
		{ list-style-image: url("throbber-16-anim.gif") !important;
		-moz-image-region: rect(0px 16px 16px 0px) !important;
		opacity: 1.0 !important; }

	#main-window[firefox3] .alltabs-item[busy][_moz-menuactive="true"]
	> .menu-iconic-left > .menu-iconic-icon
		{ -moz-image-region: rect(0px 32px 16px 16px) !important; }  


/*   =================================================================================================================   */  
 
 

/*  Use the old-style QuickFind Bar */
        .findbar-container > *
		{ display: -moz-box; }

/*  Reduce height of bookmarkbar  
	#PersonalToolbar
        	{ min-height: 26px !important;
         	max-height: 26px !important; 
        	margin-top: 0px } */
		
	/*	#toolbar-menubar {
min-height: 30px !important;
max-height: 30px !important;
margin-top: -2px !important;
}   */

 /* Bookmarks toolbar color 
    #PersonalToolbar { background: #3D3D3D !important; }*/


/* Remove bookmark toolbar folder arrows */
       #PersonalToolbar .toolbarbutton-menu-dropmarker 
       		{display: none !important;} 

/* Hide bookmarks context menuitems */ 
        menuitem[label="New Separator"],
        menuitem[label="Sort By Name"],
        menuitem[label="Open in a New Tab"],
        menuitem[label="Open All in Tabs"],
        menuitem[label="Open"],
        menuitem[command="placesCmd_new:bookmark"] 
                { display: none !important; } 
			   
/*  Hide menu separators  */
        menuseparator 
		{ display: none; }  

/*  Hide disabled menuitems  */      
        menuitem[disabled="true"],
        menuitem[disabled="true"] + menuseparator
                { display: none; }	

/* Hide hotkeys from menus */   	 	
	.menu-iconic-accel 
		{ display: none !important; }
        .menu-accel 
		{ display: none !important; }	


/*   ======================================================END========================================================   */  
```

---

### Post by Zorael on 2009-05-18
Awesome, got many ideas from that .css of yours blacksm1th, many thanks.

---

### Post by Xbehave on 2009-05-18
```
[disabled="true"], /*hides inactive buttons*/
#back-forward-dropmarker, /*hides back/forward drop marker*/
.autocomplete-history-dropmarker, /*hide the adressbar dropmarker*/
.searchbar-dropmarker-image, /*hide the search box dropmarker */
.toolbarbutton-menu-dropmarker, /*hides the bookmark menu drops*/
.search-go-button, /*hides the magnifying glass in the search bar*/
#personal-bookmarks .toolbarbutton-text, /* hide bookmark toolbar icon images */
.tabs-newtab-button
{display: none !important; }

/* change space around bookmark toolbar icons */
#personal-bookmarks toolbarbutton {
padding: 0px 5px !important;

```
If anybody knows the code to get rid of all drop markers (or even just the flashblock one, please PM moi

---

### Post by blacksm1th on 2009-05-18
> **Zorael said:**
> Awesome, got many ideas from that .css of yours blacksm1th, many thanks.
I have 2 new versions of userchrome:

[IMG]http://img172.imageshack.us/img172/3159/screenshotzhn.png[/IMG]

[IMG]http://img245.imageshack.us/img245/7720/screenshot1z.png[/IMG]

@Xbehave You can try with "DOM inspector" and "InspectorWidget" addons from [_here_]("https://addons.mozilla.org/en-US/firefox/search?q=dom&cat=all").

Attached throbber - it must be placed in same folder as userchrome.css.

---

### Post by londonali1010 on 2009-06-24
blacksm1th,

I like the rounded look of the urlbar and searchbar; can you post how to just do those two bits? I had a look through the files you posted and it was a little too much for me!

Thanks!

---

### Post by blacksm1th on 2009-06-24
Put the file "userchrome.css" (after extraction from archive) in your "/home/YourUsername/.mozilla/firefox/Nonsense.default/chrome" directory and restart Firefox.

---

### Post by Sealbhach on 2009-06-24
Don't you like new tabs? I managed to enable new tab again by changing

menuitem[command="cmd_newNavigatorTab"],  /* New Window */

to

menuitem[command="cmd_newTab"],  /* New Tab */

purely by guesswork.:)

.

---

