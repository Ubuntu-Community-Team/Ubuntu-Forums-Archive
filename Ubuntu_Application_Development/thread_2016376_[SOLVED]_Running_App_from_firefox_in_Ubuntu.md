---
title: "[SOLVED] Running App from firefox in Ubuntu"
date: 2012-07-04
forum: Ubuntu Application Development
---

### Post by mijonuha on 2012-07-04
Dear friends
I need to make a program that opens the current local html file in **gedit**. I have found some code to run a local application from your firefox browser. but the problem is that this code is written for windows. I have changed the code still it does not work for me. I put the code here. please help me correct the code:

[HTML]<html>
<head>
</head>
<body>
<p/><input type="button" width="15" value="Run Exe" onclick="RunGEdit();"/></input></p>

<script type="text/javascript">
function RunGEdit()
{
    if(navigator.userAgent.indexOf("Firefox") == -1)
    {
        alert("Currently active folder links supported only for Mozilla Firefox web browser");
        return;
    }
    netscape.security.PrivilegeManager.enablePrivilege("UniversalXPConnect");
    var localFile = 
        Components.classes["@mozilla.org/file/local;1"]
        .createInstance(Components.interfaces.nsILocalFile);
    var env =
        Components.classes["@mozilla.org/process/environment;1"]
        .createInstance(Components.interfaces.nsIEnvironment);
    localFile.initWithPath("/usr/bin/gedit");
    var process =
        Components.classes["@mozilla.org/process/util;1"]
        .createInstance(Components.interfaces.nsIProcess);
    process.init(localFile);
    process.run(false, document.URL, 1);


}
</script>
</body>
</html>[/HTML]

---

### Post by mijonuha on 2012-07-04
even though with a lot of trouble, finally i found the answer:

```
function RunGEdit()
{
    netscape.security.PrivilegeManager.enablePrivilege('UniversalXPConnect');
    var exe = Components.classes['@mozilla.org/file/local;1'].createInstance(Components.interfaces.nsILocalFile);
    exe.initWithPath("/usr/bin/gedit");
    var run = Components.classes['@mozilla.org/process/util;1'].createInstance(Components.interfaces.nsIProcess);
    run.init(exe);        
    var parameters = [document.URL];
    run.run(true, parameters,parameters.length);
}
```

---

