---
title: "Problem with include files"
date: 2009-02-02
forum: Server Platforms
---

### Post by cpetercarter on 2009-02-02
I have a php programme which uses a number of include files.

At present, the include files are in a directory within the php programme. I have added the path to the include file directory to the general php include path.

[PHP]define('INCLUDE_FILES', PATH_TO_ROOT."/podhawk/inc");

$inc = (ini_get("include_path"));
ini_set("include_path", $inc. PATH_SEPARATOR . INCLUDE_FILES);
[/PHP]

 It works fine. My programme is able to find its include files.


I would like to be able to place the include files somewhere else, however, so that they could be accessed by multiple installations of the programme on the same server. I have created a new directory 'podhawk' in /usr/local and successfully copied the 'inc' directory to it. I have then changed the first line of the code above so that it reads:

[PHP]define('INCLUDE_FILES', '/usr/local/podhawk/inc');[/PHP]

The programme adds this path to the include path; nonetheless the programme returns error messages to say that it cannot find the various include files. The directory /usr/local/podhawk/inc is owned by root with permissions set to 0755. I have tried changing the owner to www-data, and file permissions to 0777 but, not surprisingly, it makes no difference.

I guess there is something elementary which I have overlooked. Any idea what it might be?

PS: I have now run the same programme on 'localhost' on my desktop machine. I have amended the include path as above, and the programme runs fine. So the problem appears to be specific to my server.

---

### Post by cpetercarter on 2009-02-03
OK. Found it. There was a open_basedir restriction which prevented php from accessing anything outside the document root, even if it is in the include_path. I have found and amended the relevant config file, and everything now appears to work.

---

