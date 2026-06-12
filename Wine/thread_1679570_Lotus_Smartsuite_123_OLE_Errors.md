---
title: "Lotus Smartsuite 123 OLE Errors"
date: 2011-02-01
forum: Wine
---

### Post by HornedBeast on 2011-02-01
Hello,

I am trying to do a 'paste special' between a 123 spreadsheet and a Wordpro document in Lotus Smartsuite. For some reason it doesn't seem to be working at all well.

I've even installed OLE versions from Windows, but that doesn't seem to be having any luck either.

I am getting these errors whenever I try pasting OLE type objects between the programs... perhaps this will look familiar to someone.

```
fixme:ole:OleQueryLinkFromData (0x12e890),stub!
err:rpc:I_RpcReceive we got fault packet with status 0x3e6
fixme:ole:OleQueryLinkFromData (0x12e890),stub!
err:rpc:I_RpcReceive we got fault packet with status 0x3e6
fixme:ole:OleQueryLinkFromData (0x12e890),stub!
err:rpc:I_RpcReceive we got fault packet with status 0x3e6
fixme:ole:OleQueryLinkFromData (0x12e890),stub!
err:rpc:I_RpcReceive we got fault packet with status 0x3e6
fixme:ole:OleQueryLinkFromData (0x12e890),stub!
err:rpc:I_RpcReceive we got fault packet with status 0x3e6
fixme:ole:OleGetIconOfClass (0x1c1368,(nil),1), stub!
fixme:ole:OleGetIconOfClass (0x1c1398,0x33e84c,0), stub!
fixme:ole:OleQueryLinkFromData (0x12e890),stub!
fixme:ole:OleQueryLinkFromData (0x12e890),stub!
fixme:ole:OleCreateFromDataEx (0x12e890, {00000000-0000-0000-c000-000000000046}, 00000000, 00000001, 0, (nil), (nil), (nil), (nil), (nil), 0x971a68, 0x33f110): stub
fixme:ole:DefaultHandler_SetContainedObject ()
fixme:ole:OleDoAutoConvert (0x922b20,0x33f1f4) : stub
fixme:ole:DefaultHandler_SetContainedObject ()
fixme:ole:DefaultHandler_Run ((nil)): semi-stub
err:ole:marshal_object object doesn't expose interface {b722bcc7-4e68-101b-a2bc-00aa00404770}, failing with error 0x80004002
```


Any help regarding this would be appreciated.

Thank-you kindly.

---

### Post by cogadh on 2011-02-01
What exactly did you install when you say "OLE versions from Windows" and how did you install it?

---

### Post by HornedBeast on 2011-02-01
I copied the ole2.dll from my Windows install where Lotus Smartsuite runs absolutely fine.

I then correctly setup wine to use the Windows library rather than the built-in ones.

And they we're making a difference because a tick box (not relevant here really) was suddenly available and wasn't whenever I removed the DLL settings in wine.

---

### Post by cogadh on 2011-02-01
ole2.dll is just the 16 bit ole, you probably need the 32 bit. Try using [winetricks]("http://wiki.winehq.org/winetricks") to install the native dcom, it might help.

---

### Post by HornedBeast on 2011-02-10
Winetricks no longer allows you to install the latest DCOM because apparently its not needed any more as Wine has its own.

It's strange because Lotus seems to completely work, except for when using the Linked Objects (Kind of like modern day DDEs)... it just wont display data from another object.

Any other suggestions? Has anyone got Object Linking working on Lotus Smartsuite on Linux yet?

---

### Post by HornedBeast on 2011-02-10
Oh... and I am using the latest version of Wine from the Wine repos. Version 1.3.13 at time of writing.

---

