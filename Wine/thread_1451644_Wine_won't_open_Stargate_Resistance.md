---
title: "Wine won't open Stargate Resistance"
date: 2010-04-10
forum: Wine
---

### Post by JacKeown on 2010-04-10
Hi, I'm a huge Stargate fan and I just downloaded the game and installed it via wine and it all seemed to go well but nothing happened when I tried to run the Game.  I double clicked it but nothing happens. Any Ideas?

P.S. sorry if I sound very incompetent.:guitar:

---

### Post by asdfoo on 2010-04-10
> **JacKeown said:**
> Hi, I'm a huge Stargate fan and I just downloaded the game and installed it via wine and it all seemed to go well but nothing happened when I tried to run the Game.  I double clicked it but nothing happens. Any Ideas?

P.S. sorry if I sound very incompetent.:guitar:

Which Wine version?  open a terminal and type:

wine --version

It should say wine-1.1.42.  If not, you need to update.

Second.

cd to the install directory using terminal to run the program, it should provide more information about what went wrong

---

### Post by JacKeown on 2010-04-11
I updated wine, and ran the exe file in Terminal, but it says "install the Windows version of Mono to run .NET executables"....

---

### Post by gradinaruvasile on 2010-04-11
Well, install it...

[http://www.mono-project.com/Main_Page](http://www.mono-project.com/Main_Page)

---

### Post by JacKeown on 2010-04-11
I installed Mono for windows and now it works! Thanks!

---

### Post by JacKeown on 2010-04-11
I guess I spoke too soon......I double clicked it and it opens but won't let me start the game...I tried opening it in terminal and it gave me this:

Unhandled Exception: System.OverflowException: Number overflow.
  at System.Drawing.SizeF.ToSize () [0x00000] in <filename unknown>:0 
  at System.Windows.Forms.MessageBox+MessageBoxForm.InitFormsSize () [0x00000] in <filename unknown>:0 
  at System.Windows.Forms.MessageBox+MessageBoxForm.RunDialog () [0x00000] in <filename unknown>:0 
  at (wrapper remoting-invoke-with-check) System.Windows.Forms.MessageBox/MessageBoxForm:RunDialog ()
  at System.Windows.Forms.MessageBox.Show (System.String text, System.String caption, MessageBoxButtons buttons) [0x00000] in <filename unknown>:0 
  at Launcher.MainForm.CheckForUpdates () [0x00000] in <filename unknown>:0 
  at Launcher.MainForm.timer1_Tick (System.Object sender, System.EventArgs e) [0x00000] in <filename unknown>:0 
  at System.Windows.Forms.Timer.OnTick (System.EventArgs e) [0x00000] in <filename unknown>:0 
  at System.Windows.Forms.Timer.FireTick () [0x00000] in <filename unknown>:0 
  at (wrapper remoting-invoke-with-check) System.Windows.Forms.Timer:FireTick ()
  at System.Windows.Forms.XplatUIWin32.GetMessage (System.Windows.Forms.MSG& msg, IntPtr hWnd, Int32 wFilterMin, Int32 wFilterMax, Boolean blocking) [0x00000] in <filename unknown>:0 
  at System.Windows.Forms.XplatUIWin32.GetMessage (System.Object queue_id, System.Windows.Forms.MSG& msg, IntPtr hWnd, Int32 wFilterMin, Int32 wFilterMax) [0x00000] in <filename unknown>:0 
  at System.Windows.Forms.XplatUI.GetMessage (System.Object queue_id, System.Windows.Forms.MSG& msg, IntPtr hWnd, Int32 wFilterMin, Int32 wFilterMax) [0x00000] in <filename unknown>:0 
  at System.Windows.Forms.Application.RunLoop (Boolean Modal, System.Windows.Forms.ApplicationContext context) [0x00000] in <filename unknown>:0 
  at System.Windows.Forms.Application.Run (System.Windows.Forms.ApplicationContext context) [0x00000] in <filename unknown>:0 
  at System.Windows.Forms.Application.Run (System.Windows.Forms.Form mainForm) [0x00000] in <filename unknown>:0 
  at Launcher.Program.Main () [0x00000] in <filename unknown>:0

---

### Post by JacKeown on 2010-04-11
If I double click the .desktop file on my desktop it shows the normal screen to press play but it says "Checking for Updates" and never finishes...and It's the latest version of wine and the game...I can click the other buttons on the program and they work but the "play" button doesn't work.....any ideas?

---

