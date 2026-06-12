---
title: "MonoDevelop error on startup"
date: 2006-06-17
forum: Ubuntu Backports
---

### Post by Dybber on 2006-06-17
Hi

I've just installed Mono and MonoDevelop through Synaptic, but I'm getting the following error when I launch MonoDevelop:

```
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.FormatException: Index (zero based) must be greater than or equal to zero and less than the size of the argument list.
in <0x004e3> System.String:FormatHelper (System.Text.StringBuilder result, IFormatProvider provider, System.String format, System.Object[] args)
in <0x0002b> System.String:Format (IFormatProvider provider, System.String format, System.Object[] args)
in <0x00037> System.String:Format (System.String format, System.Object arg0)
in <0x00047> MonoDevelop.Ide.Gui.Pads.OpenTaskView:UpdateErrorsNum ()
in <0x000da> MonoDevelop.Ide.Gui.Pads.OpenTaskView:.ctor ()
in <0x00000> <unknown method>
in (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[])
in <0x0008d> System.Reflection.MonoCMethod:Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)--- End of inner exception stack trace ---

in <0x0010e> System.Reflection.MonoCMethod:Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)
in <0x0001c> System.Reflection.MonoCMethod:Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)
in <0x00035> System.Reflection.ConstructorInfo:Invoke (System.Object[] parameters)
in <0x00105> System.Activator:CreateInstance (System.Type type, Boolean nonPublic)
in <0x0000c> System.Activator:CreateInstance (System.Type type)
in <0x0001f> MonoDevelop.Core.AddIns.AddIn:CreateObject (System.String className)
in <0x00083> MonoDevelop.Ide.Codons.PadCodon:CreatePad ()
in <0x00014> MonoDevelop.Ide.Codons.PadCodon:BuildItem (System.Object owner, System.Collections.ArrayList subItems, MonoDevelop.Core.AddIns.ConditionCollection conditions)
in <0x00158> MonoDevelop.Core.AddIns.DefaultAddInTreeNode:BuildChildItems (System.Object caller)
in <0x00069> MonoDevelop.Core.AddIns.AddInService:GetTreeItems (System.String path, System.Type itemType)
in <0x0005c> MonoDevelop.Ide.Gui.DefaultWorkbench:InitializeLayout (IWorkbenchLayout workbenchLayout)
in <0x000a3> MonoDevelop.Ide.Gui.Workbench:Initialize (IProgressMonitor monitor)
in <0x000b1> MonoDevelop.Ide.Gui.IdeApp:Initialize (IProgressMonitor monitor)
in <0x008ad> MonoDevelop.Ide.Gui.IdeStartup:Run (System.String[] args)
```

I read this other thread: [http://ubuntuforums.org/showthread.php?p=249653](http://ubuntuforums.org/showthread.php?p=249653)

He suggest to install monodoc-base, but it doesn't help in my case.

What else could be the problem?

Best regards,
Dybber

---

### Post by IrIT on 2006-06-27
I've just installed Monodevelop to (Ubuntu 6.06). And I'm getting the exact same error :(

---

### Post by bunny64 on 2006-07-10
> **IrIT said:**
> I've just installed Monodevelop to (Ubuntu 6.06). And I'm getting the exact same error :(

Similar stuff here. It worked to start with, but then I changed the layout slightly and even after removing/reinstalling all trace of it I still get the same errors.

Running 6.06 x86_64 on a AMD Athlon XP 64.

```
bunny64@bunny64-desktop:~$ monodevelop

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries
used by your application.
=================================================================

Stacktrace:

in (wrapper managed-to-native) Gecko.WebControl:gtk_moz_embed_render_data (intptr,intptr,uint,intptr,intptr) <0xe>
in (wrapper managed-to-native) Gecko.WebControl:gtk_moz_embed_render_data (intptr,intptr,uint,intptr,intptr) <0xffffffffffffffa3>
in Gecko.WebControl:RenderData (string,string,string) <0x83>
in MonoDevelop.Components.HtmlControl.MozillaControl:InitializeWithBase (string) <0x3a>
in MonoDevelop.Components.HtmlControl.MozillaControl:DelayedInitialize () <0x1a>in MonoDevelop.WelcomePage.WelcomePageView:Initialize (object) <0x20>
in MonoDevelop.WelcomePage.ShowWelcomePageOnStartUpHandler:Run () <0x95>
in (wrapper runtime-invoke) System.Object:runtime_invoke_void (object,intptr,intptr,intptr) <0x696e72a9>
in (wrapper managed-to-native) System.Reflection.MonoMethod:InternalInvoke (object,object[]) <0xb>
in (wrapper managed-to-native) System.Reflection.MonoMethod:InternalInvoke (object,object[]) <0xfffffffffffff982>
in System.Reflection.MonoMethod:Invoke (object,System.Reflection.BindingFlags,System.Reflection.Binder,object[],System.Globalization.CultureInfo) <0xda>
in System.Reflection.MethodBase:Invoke (object,object[]) <0x34>
in MonoDevelop.Ide.Gui.IdeApp:Initialize (MonoDevelop.Core.IProgressMonitor) <0x6c8>
in MonoDevelop.Ide.Gui.IdeStartup:Run (string[]) <0xb2d>
in MonoDevelop.Core.AddIns.AddInService:StartApplication (string,string[]) <0x1ff>
in MonoDevelop.Startup.SharpDevelopMain:Main (string[]) <0x54>
in (wrapper runtime-invoke) System.Object:runtime_invoke_int_string[] (object,intptr,intptr,intptr) <0x6ac85dd5>

Native stacktrace:

        /usr/lib/libmono.so.0(mono_handle_native_sigsegv+0xa0) [0x2aaaaac565e0]
        /usr/lib/libmono.so.0 [0x2aaaaac19be8]
        /lib/libpthread.so.0 [0x2aaaab4874d0]
        /usr/lib/firefox/libgtkembedmoz.so [0x2aaab4d20dde]
        /usr/lib/firefox/libgtkembedmoz.so(gtk_moz_embed_render_data+0x6b) [0x2aaab4d1e7db]
        [0x422900a3]
```

Is there any way to swap the firefox libaries to Swiftfox's? (/opt/swiftfox...)

EDIT: Fixed it by simply moving swiftfox and all it's libaries into /usr/lib/firefox

---

### Post by Dybber on 2006-09-22
Ok the problem is solved now. Its a bug in my locale da_DK. To avoid it, simply start monodevelop with the command:

```
LANG=en_US monodevelop
```

Or install monodevelop from SVN.

---

