---
title: "Microsoft swipes some GPL code without permission"
date: 2009-11-07
forum: The Cafe
---

### Post by phrostbyte on 2009-11-07
Let's be realistic here, it was probably an honest mistake. 8-[

[http://www.withinwindows.com/2009/11/06/microsoft-lifts-gpl-code-uses-in-microsoft-store-tool/](http://www.withinwindows.com/2009/11/06/microsoft-lifts-gpl-code-uses-in-microsoft-store-tool/)

> 
While poking through the UDF-related internals of the Windows 7 USB/DVD Download Tool, I had a weird feeling there was just wayyyyyyyyy too much code in there for such a simple tool. A simple search of some method names and properties, gleaned from Reflector&#8217;s output, revealed the source code was obviously lifted from the CodePlex-hosted (yikes) GPLv2-licensed ImageMaster project. (The author of the code was not contacted by Microsoft.)

---

### Post by pwnst*r on 2009-11-08
been posted.  also, blown out of proportion.  typical.

---

### Post by phrostbyte on 2009-11-08
If it was already posted why did you bump this when is was off the main page? [-(

---

### Post by Perfect Storm on 2009-11-08
> !!!! I can't edit the title, it is suppose to be Microsoft swipes some GPL code without permission

Done.

---

### Post by phrostbyte on 2009-11-08
> **Artificial Intelligence said:**
> Done.

Thank you! :p

---

### Post by pwnst*r on 2009-11-08
cuz i felt like it? 

actually, didn't realize i was on the 2nd or 3rd. i was looking for something.

---

### Post by phrostbyte on 2009-11-08
> **pwnst*r said:**
> cuz i felt like it? 

actually, didn't realize i was on the 2nd or 3rd. i was looking for something.

Good enough reason I guess.

---

### Post by pwnst*r on 2009-11-08
there's no guessing.  it's a good reason.

---

### Post by pwnst*r on 2009-11-08
oh, and

[http://ubuntuforums.org/showthread.php?t=1318255&highlight=slashdot](http://ubuntuforums.org/showthread.php?t=1318255&highlight=slashdot)

---

### Post by phrostbyte on 2009-11-08
> **pwnst*r said:**
> oh, and

[http://ubuntuforums.org/showthread.php?t=1318255&highlight=slashdot](http://ubuntuforums.org/showthread.php?t=1318255&highlight=slashdot)

Whatever the hell that was talking about is wrong. If you go to that blog post, it's become clear that isn't just one method (ReadBytes) 

The only argument people have is that perhaps the code comes from another mysterious project which Microsoft can legally use code from. But I guess we can not know for sure until the author of ImageMaster speaks up. I hope he is fairly compensated if this turns out to be true. :)

---

### Post by Icehuck on 2009-11-08
> **phrostbyte said:**
> Whatever the hell that was talking about is wrong. If you go to that blog post, it's become clear that isn't just one method (ReadBytes) 

The only argument people have is that perhaps the code comes from another mysterious project which Microsoft can legally use code from. But I guess we can not know for sure until the author of ImageMaster speaks up. I hope he is fairly compensated if this turns out to be true. :)

Show me the code line for line and I'll believe you. The author of the blog never actually proves it, but say's he leaves it up to the readers to do so.

---

### Post by phrostbyte on 2009-11-08
> **Icehuck said:**
> Show me the code line for line and I'll believe you. The author of the blog never actually proves it, but say's he leaves it up to the readers to do so.

[http://www.withinwindows.com/wp-content/uploads/2009/11/example1.png](http://www.withinwindows.com/wp-content/uploads/2009/11/example1.png)

Notice how that is not ReadBytes

More code:

[http://www.withinwindows.com/files/gpl/comparison_1.txt](http://www.withinwindows.com/files/gpl/comparison_1.txt)

How much code is needed to prove a violation? I am not a lawyer. :)

---

### Post by Frak on 2009-11-08
> **phrostbyte said:**
> [http://www.withinwindows.com/wp-content/uploads/2009/11/example1.png](http://www.withinwindows.com/wp-content/uploads/2009/11/example1.png)

Notice how that is not ReadBytes

More code:

[http://www.withinwindows.com/files/gpl/comparison_1.txt](http://www.withinwindows.com/files/gpl/comparison_1.txt)

How much code is needed to prove a violation? I am not a lawyer. :)
That's not nearly enough. One or two methods won't be considered enough proof. The rule is if the program emulates the entire logic and goal of another program, then it is theft. Something like this, which is just a simple method, would be considered nothing more than coincidence or canonical methodology.

---

### Post by phrostbyte on 2009-11-08
> **Frak said:**
> That's not nearly enough. One or two methods won't be considered enough proof. The rule is if the program emulates the entire logic and goal of another program, then it is theft. Something like this, which is just a simple method, would be considered nothing more than coincidence or canonical methodology.

I'll have to disagree for now.

---

### Post by Frak on 2009-11-08
> **phrostbyte said:**
> I'll have to disagree for now.
Code theft is incredibly hard to prove in court. CherryPC was the last project that could, without a doubt, be proven in court.

---

### Post by Chronon on 2009-11-08
> **Frak said:**
> That's not nearly enough. One or two methods won't be considered enough proof. The rule is if the program emulates the entire logic and goal of another program, then it is theft. Something like this, which is just a simple method, would be considered nothing more than coincidence or canonical methodology.

I don't see how that can possibly be the case.  Emulating what another program does is totally legal and legit (barring patents or the like).  Copyright only protects the form, not the function of a program's code.  I do agree that existence of a few common strings is probably not enough to demonstrate a copyright violation.

---

### Post by Frak on 2009-11-08
> **Chronon said:**
> I don't see how that can possibly be the case.  Emulating what another program does is totally legal and legit (barring patents or the like).  Copyright only protects the form, not the function of a program's code.  I do agree that existence of a few common strings is probably not enough to demonstrate a copyright violation.
By emulate, I mean entire theft of code.

---

### Post by phrostbyte on 2009-11-08
> **Frak said:**
> Code theft is incredibly hard to prove in court. CherryPC was the last project that could, without a doubt, be proven in court.

If there is reasonable assumption that they may have swiped this gentleman's code, I think Microsoft would be generous enough to take steps to obtain a license and compensate the author for his efforts and in proportion to their mistake. Despite Microsoft's disrespect of the GPL, I do believe they respect copyright law and the right of a software developer to control unauthorized use of their work, which this may be just one example of.

---

### Post by Frak on 2009-11-08
> **phrostbyte said:**
> If there is reasonable assumption that they may have swiped this gentleman's code, I think Microsoft would be generous enough to take steps to obtain a license and compensate the author for his efforts and in proportion to their mistake. Despite Microsoft's disrespect of the GPL, I do believe they respect copyright law and the right of a software developer to control unauthorized use of their work, which this may be just one example of.
I'm going to go with the 3rd party studio on this one. I doubt Microsoft would swipe code. There's massive code audits on internal code every so often. I'll go with the same thing that happened with the Windows XP sound files, Microsoft handed the duty to a 3rd party studio and they decided to take the easy way out and swipe code.

I still say this is blown out of proportion.

---

### Post by lethalfang on 2009-11-08
> **phrostbyte said:**
> **If there is reasonable assumption that they may have swiped this gentleman's code, I think Microsoft would be generous enough to take steps to obtain a license and compensate the author for his efforts and in proportion to their mistake.** Despite Microsoft's disrespect of the GPL, I do believe they respect copyright law and the right of a software developer to control unauthorized use of their work, which this may be just one example of.

Except that, once you have released your code under GPL, you cannot un-GPL it.

---

### Post by Frak on 2009-11-08
> **lethalfang said:**
> Except that, once you have released your code under GPL, you cannot un-GPL it.
Current releases, no, future releases, yes.

---

### Post by phrostbyte on 2009-11-13
New news on this. :)

Microsoft has admitted that they took GPL code without permission and has in turn released their entire codebase for this tool under the GPL:

[http://community.winsupersite.com/blogs/paul/archive/2009/11/13/rafael-is-vindicated-microsoft-did-steal-open-source-code-for-usb-dvd-tool.aspx](http://community.winsupersite.com/blogs/paul/archive/2009/11/13/rafael-is-vindicated-microsoft-did-steal-open-source-code-for-usb-dvd-tool.aspx)

---

### Post by Sealbhach on 2009-11-13
> **phrostbyte said:**
> New news on this. :)

Microsoft has admitted that they took GPL code without permission and has in turn released their entire codebase for this tool under the GPL:

[http://community.winsupersite.com/blogs/paul/archive/2009/11/13/rafael-is-vindicated-microsoft-did-steal-open-source-code-for-usb-dvd-tool.aspx](http://community.winsupersite.com/blogs/paul/archive/2009/11/13/rafael-is-vindicated-microsoft-did-steal-open-source-code-for-usb-dvd-tool.aspx)

Looks like Microsoft is getting more and more contaminated by freedom.

.

---

### Post by phrostbyte on 2009-11-13
> **Sealbhach said:**
> Looks like Microsoft is getting more and more contaminated by freedom.

.

Indeed. :lolflag:

---

### Post by Frak on 2009-11-13
> **Sealbhach said:**
> Looks like Microsoft is getting more and more contaminated by freedom.

.
Looks like that 3rd party studio is about to feel the iron palm of Microsoft's lawyers.

---

### Post by earthpigg on 2009-11-13
> **Sealbhach said:**
> Looks like Microsoft is getting more and more contaminated by freedom.

ammunition for future claims that the GPL is a 'cancer' that 'infects' software.

---

### Post by wilee-nilee on 2009-11-13
You can't get the link to the dvd-thumb anymore but just yesterday I was able to download into another computer with the link I saved. I haven't tried to see if it still works even though I have a W7 DVD my thumb is loaded already with the original use I am not going to wipe it to see if the program still works.

---

### Post by phrostbyte on 2009-12-07
Another update on this (a bit late):

[http://port25.technet.com/archive/2009/11/20/update-on-the-windows-7-usb-dvd-tool.aspx](http://port25.technet.com/archive/2009/11/20/update-on-the-windows-7-usb-dvd-tool.aspx)

Microsoft seems to be delaying the release of this source code. They give no indication when it will actually be released.

---

### Post by Frak on 2009-12-07
> **phrostbyte said:**
> Another update on this (a bit late):

[http://port25.technet.com/archive/2009/11/20/update-on-the-windows-7-usb-dvd-tool.aspx](http://port25.technet.com/archive/2009/11/20/update-on-the-windows-7-usb-dvd-tool.aspx)

Microsoft seems to be delaying the release of this source code. They give no indication when it will actually be released.
It's a conspiracy!

---

### Post by phrostbyte on 2009-12-07
> **Frak said:**
> It's a conspiracy!

Probably.

---

### Post by alexfish on 2009-12-07
History  / part1

 The next time Bill Gates sends an e-mail through Microsoft&#8217;s shiny new Wireless LAN it will be passed through a behind-the-scenes Linux-based network appliance.
 Earlier this year Microsoft and Aruba Networks jointly announced the two companies will work to replace Microsoft&#8217;s existing Cisco wireless network with Aruba&#8217;s centrally-managed infrastructure, which eliminates the need for individual changes on the access points.
 Aruba Networks was selected to provide the networking equipment for what is considered to be one of the world&#8217;s largest next-generation wireless LANs, serving more than 25,000 simultaneous users a day in some 60 countries. According to an Aruba press statement, Microsoft&#8217;s new WLAN will be deployed in 277 buildings covering more than 17 million square feet using Aruba mobility controllers, mobility software and some 5000 wireless access points.


So Linux Works / Wonder if they made a donation / and have copies of the GNU General Public License

history/ part 2

Seems they don't have them

   so posted this on their new site Forum
[http://www.linux.org/info/gnu.html](http://www.linux.org/info/gnu.html)

History /part 3

 the story behind part 2

Linux /mobile broadband  / site restricted / used friends   Phenom X4 9850 system / xp

site not restricted  / posted // then had coffee / Smashed the dongle

---

### Post by phrostbyte on 2009-12-10
They finally released the code.

[http://wudt.codeplex.com/](http://wudt.codeplex.com/)

Unfortunately it contains unmanaged (C++) libraries which are written to be heavily dependent on Win32. I didn't look at it so hard, but it's probably difficult to port to Linux.

It might however be useful as a ISO -> USB Drive creator for Windows. I have to commend Microsoft, it has a very nice UI. This could even replace the Windows-based USB tool that is bundled with Ubuntu. :)

---

### Post by Frak on 2009-12-10
> **phrostbyte said:**
> Unfortunately it contains unmanaged (C++) libraries which are written to be heavily dependent on Win32. I didn't look at it so hard, but it's probably difficult to port to Linux.

CoolStoryBro

---

### Post by phrostbyte on 2009-12-10
> **Frak said:**
> CoolStoryBro

Do you have anything productive to add to this thread?

---

### Post by Frak on 2009-12-10
> **phrostbyte said:**
> Do you have anything productive to add to this thread?
No, other than:

"Wow, Microsoft having code that is heavily tied to Windows? That's new!"

---

### Post by murderslastcrow on 2009-12-10
I wonder why this hasn't been marked as recurring discussion. ^_~ LOLZ!

The day to hide behind your dominance is ending fast for Microsoft. I can see it all around me.

---

### Post by phrostbyte on 2009-12-10
> **murderslastcrow said:**
> I wonder why this hasn't been marked as recurring discussion. ^_~ LOLZ!

The day to hide behind your dominance is ending fast for Microsoft. I can see it all around me.

Actually I'd like this to be moved to Programming Talk, if possible, now that Microsoft released the source code.

---

### Post by phrostbyte on 2009-12-10
The code does a total of six native calls.

```

MainForm.cs/NativeMethods
-------------------

            /// <summary>
            /// The send message method for allowing the window to be dragable.
            /// </summary>
            /// <param name="hWnd">The window handle.</param>
            /// <param name="msg">The message to send.</param>
            /// <param name="wParam">The wParam value.</param>
            /// <param name="lParam">The lParam value.</param>
            /// <returns>The hResult of the call.</returns>
            [DllImport("user32.dll")]
            public static extern IntPtr SendMessage(IntPtr hWnd, int msg, IntPtr wParam, IntPtr lParam);

            /// <summary>
            /// Releases the window caputre.
            /// </summary>
            /// <returns>True on success.</returns>
            [DllImport("user32.dll")]
            [return: MarshalAs(UnmanagedType.Bool)]
            public static extern bool ReleaseCapture();

            /// <summary>
            /// Sets the execution state for allowing the tool to disable standby (Vista and higher).
            /// </summary>
            /// <param name="esFlags">The flags indicating the thread execution state.</param>
            /// <returns>The execution state that was set.</returns>
            [DllImport("kernel32.dll")]
            public static extern EXECUTION_STATE SetThreadExecutionState(EXECUTION_STATE esFlags);

            /// <summary>
            /// Gets the integer value for the given window message.
            /// </summary>
            /// <param name="msgString">The window message to lookup.</param>
            /// <returns>The integer value for the message.</returns>
            [DllImport("user32", CharSet = CharSet.Auto)]
            private static extern int RegisterWindowMessage([In, MarshalAs(UnmanagedType.LPWStr)] string msgString);

USBDriveService/NativeMethods
-----------------------------

            /// <summary>
            /// Sets the active partition.
            /// </summary>
            /// <param name="drive">The root path of the drive to update.</param>
            /// <returns>Returns 0 for success.  See System Error Codes for possible error values.</returns>
            [DllImport("IoWrapper.dll", CharSet = CharSet.Auto)]
            public static extern int SetActivePartition([In, MarshalAs(UnmanagedType.LPWStr)] string drive);

            /// <summary>
            /// Formats the drive.
            /// </summary>
            /// <param name="drive">The root path of the drive to update.</param>
            /// <returns>Returns 0 for success.  See System Error Codes for possible error values.</returns>
            [DllImport("IoWrapper.dll", CharSet = CharSet.Auto)]
            public static extern int FormatDrive([In, MarshalAs(UnmanagedType.LPWStr)] string drive);

```

The obvious question would be:
Does anyone know what native calls or Mono methods to replace these methods, so that it will compile under Linux?

---

### Post by red_Marvin on 2009-12-10
> **lethalfang said:**
> Except that, once you have released your code under GPL, you cannot un-GPL it.
AFAIK the GPL does not stop the original developer of a piece of code to dual license it etc.

---

### Post by Frak on 2009-12-10
> **red_Marvin said:**
> AFAIK the GPL does not stop the original developer of a piece of code to dual license it etc.
Exactly. The original developer could have said "It is OK for Microsoft not to release the source" and that would be the end of the discussion. Microsoft could have paid the developer to let them go without releasing the source code, which I don't doubt Microsoft has done in the past. They didn't, which was wise. The project didn't have any real value to Microsoft, but even then, it's cheaper to buy working code than to build it again yourself.

---

### Post by wilee-nilee on 2009-12-10
It has been re-released available at the MS store and here.
[http://wudt.codeplex.com/](http://wudt.codeplex.com/)

---

### Post by phrostbyte on 2009-12-10
I managed to get the tool to accept an Ubuntu ISO. :guitar:

Don't get to excited though, I did it in a hackish way (changed something from "false" to "true"). I want to figure out the 'right' way. :)

I've pinpointed the issue so far to this block of code
```

            VolumeTag tag = new VolumeTag();
            if (tag.Parse(0, buffer, buffer.Length)
                && tag.Identifier == (short)VolumeDescriptorType.AnchorVolumePtr)
            {
                result = new UdfFileExtent();
                result.Parse(16, buffer);
            }

```

Not sure what VolumeTag.Parse or VolumeTag.Identifier is suppose to mean in this context.

---

