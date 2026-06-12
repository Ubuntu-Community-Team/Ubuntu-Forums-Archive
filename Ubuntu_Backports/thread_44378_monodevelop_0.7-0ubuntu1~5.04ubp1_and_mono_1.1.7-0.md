---
title: "monodevelop 0.7-0ubuntu1~5.04ubp1 and mono 1.1.7-0ubuntu4~5.04ubp1 dependency issue"
date: 2005-06-25
forum: Ubuntu Backports
---

### Post by aguirrel on 2005-06-25
Hi,

I have installed monodevelop 0.7-0ubuntu1~5.04ubp1 and mono 1.1.7-0ubuntu4~5.04ubp1. 
When I run monodevelop I get the following error

-------------------------------------------------------------------------------
** (MonoDevelop:31255): WARNING **: The following assembly referenced from /usr/lib/monodevelop/bin/MonoDevelop.Base.dll could not be loaded:
     Assembly:   monodoc    (assemblyref_index=8)
     Version:    1.0.0.0
     Public Key: 0738eb9f132ed756
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/monodevelop/bin).


** (MonoDevelop:31255): WARNING **: The class Monodoc.RootTree could not be loaded, used in /usr/lib/monodevelop/bin/MonoDevelop.Base.dll (token 0x01000063)

** (MonoDevelop:31255): WARNING **: Missing method LoadTree in assembly /usr/lib/monodevelop/bin/MonoDevelop.Base.dll, type Monodoc.RootTree
Loading error, please reinstall :
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.NullReferenceException: Object reference not set to an instance of an object
in <0x00000> <unknown method>
in (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[])
in <0x0006f> System.Reflection.MonoCMethod:Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)--- End of inner exception stack trace ---

in <0x00104> System.Reflection.MonoCMethod:Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)
in <0x00019> System.Reflection.MonoCMethod:Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)
in <0x00032> System.Reflection.ConstructorInfo:Invoke (System.Object[] parameters)
in <0x000e2> System.Activator:CreateInstance (System.Type type, Boolean nonPublic)
in <0x0000c> System.Activator:CreateInstance (System.Type type)
in <0x0003a> System.Reflection.Assembly:CreateInstance (System.String typeName, Boolean ignoreCase)
in <0x00012> System.Reflection.Assembly:CreateInstance (System.String typeName)
in <0x000af> MonoDevelop.Core.AddIns.AddIn:CreateObject (System.String className)
in <0x00030> MonoDevelop.Core.AddIns.Codons.ClassCodon:BuildItem (System.Object owner, System.Collections.ArrayList subItems, MonoDevelop.Core.AddIns.Conditions.ConditionCollection conditions)
in <0x0014f> MonoDevelop.Core.AddIns.DefaultAddInTreeNode:BuildChildItems (System.Object caller)
in <0x0004c> MonoDevelop.Core.Services.ServiceManager:InitializeServicesSubsystem (System.String servicesPath)
in <0x00640> MonoDevelop.SharpDevelopMain:Main (System.String[] args)
----------------------------------------------------------------------

BUT if you install monodoc-base 1.0.4-1 it works fine.  So, there are a dependency issue there.  ;-) 

Really thanks for the work you do day by day :-) It's tremendusly usefull.

Best regards,

Luis

---

### Post by amerigo5 on 2005-06-26
I had the same issue. Installing the monodoc-base fixed it. Finally, I can try the lastest version of Monodevelop!!!

---

### Post by yoda on 2005-06-27
I have the same problem with the exact same instalation as described in the title of the thread. What is strange, in my case, is that even after installing monodoc-base 1.0.4-1 I still get the same error.

I also suspect that this is the reason I can't successfully run Beagle.

Can anyone give me some advice?

---

### Post by nehalem on 2005-06-27
Well mine will kind of work but I can't use MD to create projects.   Sometimes it spits out errors and sometimes it doesn't but it still doesn't create a project.  No idea what is up...

---

### Post by ramos289 on 2005-07-11
I just had this very same problem and installing monodoc-base 1.0.4-1 didn't fix it.  However, deleting the ~/.config/MonoDevelop directory worked like a charm.  Give that a shot and see if it works for you.

---

### Post by creo on 2005-08-03
i just install monodoc, and ready

---

