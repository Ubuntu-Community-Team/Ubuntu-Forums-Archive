---
title: "Keepass2 problem under mir"
date: 2013-09-25
forum: Ubuntu Development Version
---

### Post by nickmcg on 2013-09-25
Hi,

I am unable to run keypass2 under mir, although it works ok if I revert to 'old-style' X-server.
I don't know if this is keypass itself or mono.

Trying to run from terminal gives the following:
```
Unhandled Exception: System.ArgumentException: A null reference or invalid value was found [GDI+ status: InvalidParameter]
  at System.Drawing.GDIPlus.CheckStatus (Status status) [0x00000] in <filename unknown>:0 
  at System.Drawing.Bitmap..ctor (Int32 width, Int32 height, PixelFormat format) [0x00000] in <filename unknown>:0 
  at System.Drawing.Bitmap..ctor (System.Drawing.Image original, Int32 width, Int32 height) [0x00000] in <filename unknown>:0 
  at System.Drawing.Bitmap..ctor (System.Drawing.Image original, Size newSize) [0x00000] in <filename unknown>:0 
  at (wrapper remoting-invoke-with-check) System.Drawing.Bitmap:.ctor (System.Drawing.Image,System.Drawing.Size)
  at System.Windows.Forms.XplatUIX11.DefineCursor (System.Drawing.Bitmap bitmap, System.Drawing.Bitmap mask, Color cursor_pixel, Color mask_pixel, Int32 xHotSpot, Int32 yHotSpot) [0x00000] in <filename unknown>:0 
  at System.Windows.Forms.XplatUI.DefineCursor (System.Drawing.Bitmap bitmap, System.Drawing.Bitmap mask, Color cursor_pixel, Color mask_pixel, Int32 xHotSpot, Int32 yHotSpot) [0x00000] in <filename unknown>:0 
  at System.Windows.Forms.Cursor.CreateCursor (System.IO.Stream stream) [0x00000] in <filename unknown>:0 
  at System.Windows.Forms.Cursor..ctor (System.Type type, System.String resource) [0x00000] in <filename unknown>:0 
  at System.Windows.Forms.Cursors.get_SizeNWSE () [0x00000] in <filename unknown>:0 
  at System.Windows.Forms.SizeGrip..ctor (System.Windows.Forms.Control CapturedControl) [0x00000] in <filename unknown>:0 
  at (wrapper remoting-invoke-with-check) System.Windows.Forms.SizeGrip:.ctor (System.Windows.Forms.Control)
  at System.Windows.Forms.ScrollableControl.CreateScrollbars () [0x00000] in <filename unknown>:0 
  at System.Windows.Forms.ScrollableControl..ctor () [0x00000] in <filename unknown>:0 
  at System.Windows.Forms.ContainerControl..ctor () [0x00000] in <filename unknown>:0 
  at System.Windows.Forms.Form..ctor () [0x00000] in <filename unknown>:0 
  at System.Windows.Forms.MessageBox+MessageBoxForm..ctor (IWin32Window owner, System.String text, System.String caption, MessageBoxButtons buttons, MessageBoxIcon icon, Boolean displayHelpButton) [0x00000] in <filename unknown>:0 
  at System.Windows.Forms.MessageBox+MessageBoxForm..ctor (IWin32Window owner, System.String text, System.String caption, MessageBoxButtons buttons, MessageBoxIcon icon, MessageBoxDefaultButton defaultButton, MessageBoxOptions options, Boolean displayHelpButton) [0x00000] in <filename unknown>:0 
  at (wrapper remoting-invoke-with-check) System.Windows.Forms.MessageBox/MessageBoxForm:.ctor (System.Windows.Forms.IWin32Window,string,string,System.Windows.Forms.MessageBoxButtons,System.Windows.Forms.MessageBoxIcon,System.Windows.Forms.MessageBoxDefaultButton,System.Windows.Forms.MessageBoxOptions,bool)
  at System.Windows.Forms.MessageBox.Show (System.String text, System.String caption, MessageBoxButtons buttons, MessageBoxIcon icon, MessageBoxDefaultButton defaultButton) [0x00000] in <filename unknown>:0 
  at KeePassLib.Utility.MessageService.SafeShowMessageBox (System.String strText, System.String strTitle, MessageBoxButtons mb, MessageBoxIcon mi, MessageBoxDefaultButton mdb) [0x00000] in <filename unknown>:0 
  at KeePassLib.Utility.MessageService.ShowFatal (System.Object[] vLines) [0x00000] in <filename unknown>:0 
  at KeePass.Program.Main (System.String[] args) [0x00000] in <filename unknown>:0 
[ERROR] FATAL UNHANDLED EXCEPTION: System.ArgumentException: A null reference or invalid value was found [GDI+ status: InvalidParameter]
  at System.Drawing.GDIPlus.CheckStatus (Status status) [0x00000] in <filename unknown>:0 
  at System.Drawing.Bitmap..ctor (Int32 width, Int32 height, PixelFormat format) [0x00000] in <filename unknown>:0 
  at System.Drawing.Bitmap..ctor (System.Drawing.Image original, Int32 width, Int32 height) [0x00000] in <filename unknown>:0 
  at System.Drawing.Bitmap..ctor (System.Drawing.Image original, Size newSize) [0x00000] in <filename unknown>:0 
  at (wrapper remoting-invoke-with-check) System.Drawing.Bitmap:.ctor (System.Drawing.Image,System.Drawing.Size)
  at System.Windows.Forms.XplatUIX11.DefineCursor (System.Drawing.Bitmap bitmap, System.Drawing.Bitmap mask, Color cursor_pixel, Color mask_pixel, Int32 xHotSpot, Int32 yHotSpot) [0x00000] in <filename unknown>:0 
  at System.Windows.Forms.XplatUI.DefineCursor (System.Drawing.Bitmap bitmap, System.Drawing.Bitmap mask, Color cursor_pixel, Color mask_pixel, Int32 xHotSpot, Int32 yHotSpot) [0x00000] in <filename unknown>:0 
  at System.Windows.Forms.Cursor.CreateCursor (System.IO.Stream stream) [0x00000] in <filename unknown>:0 
  at System.Windows.Forms.Cursor..ctor (System.Type type, System.String resource) [0x00000] in <filename unknown>:0 
  at System.Windows.Forms.Cursors.get_SizeNWSE () [0x00000] in <filename unknown>:0 
  at System.Windows.Forms.SizeGrip..ctor (System.Windows.Forms.Control CapturedControl) [0x00000] in <filename unknown>:0 
  at (wrapper remoting-invoke-with-check) System.Windows.Forms.SizeGrip:.ctor (System.Windows.Forms.Control)
  at System.Windows.Forms.ScrollableControl.CreateScrollbars () [0x00000] in <filename unknown>:0 
  at System.Windows.Forms.ScrollableControl..ctor () [0x00000] in <filename unknown>:0 
  at System.Windows.Forms.ContainerControl..ctor () [0x00000] in <filename unknown>:0 
  at System.Windows.Forms.Form..ctor () [0x00000] in <filename unknown>:0 
  at System.Windows.Forms.MessageBox+MessageBoxForm..ctor (IWin32Window owner, System.String text, System.String caption, MessageBoxButtons buttons, MessageBoxIcon icon, Boolean displayHelpButton) [0x00000] in <filename unknown>:0 
  at System.Windows.Forms.MessageBox+MessageBoxForm..ctor (IWin32Window owner, System.String text, System.String caption, MessageBoxButtons buttons, MessageBoxIcon icon, MessageBoxDefaultButton defaultButton, MessageBoxOptions options, Boolean displayHelpButton) [0x00000] in <filename unknown>:0 
  at (wrapper remoting-invoke-with-check) System.Windows.Forms.MessageBox/MessageBoxForm:.ctor (System.Windows.Forms.IWin32Window,string,string,System.Windows.Forms.MessageBoxButtons,System.Windows.Forms.MessageBoxIcon,System.Windows.Forms.MessageBoxDefaultButton,System.Windows.Forms.MessageBoxOptions,bool)
  at System.Windows.Forms.MessageBox.Show (System.String text, System.String caption, MessageBoxButtons buttons, MessageBoxIcon icon, MessageBoxDefaultButton defaultButton) [0x00000] in <filename unknown>:0 
  at KeePassLib.Utility.MessageService.SafeShowMessageBox (System.String strText, System.String strTitle, MessageBoxButtons mb, MessageBoxIcon mi, MessageBoxDefaultButton mdb) [0x00000] in <filename unknown>:0 
  at KeePassLib.Utility.MessageService.ShowFatal (System.Object[] vLines) [0x00000] in <filename unknown>:0 
  at KeePass.Program.Main (System.String[] args) [0x00000] in <filename unknown>:0 

```

Any ideas?

Should it be reported as a bug?

Thanks

Nick

---

### Post by mc4man on 2013-09-25
For starters i'd file a bug on keepass, providing a bit more info as to any options you've enabled past the default ones.
(first  ck. in /var/crash & see if a .crash  was created for keepass or mono. If so use that .crash file to report with

---

### Post by nickmcg on 2013-09-25
Thanks, I'll do that.

I've also found a similar problem with ubuntu tweak though.

Cheers

---

