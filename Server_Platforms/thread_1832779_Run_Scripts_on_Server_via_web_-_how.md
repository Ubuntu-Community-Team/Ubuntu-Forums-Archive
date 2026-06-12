---
title: "Run Scripts on Server via web - how?"
date: 2011-08-25
forum: Server Platforms
---

### Post by Sam Goodspeed on 2011-08-25
Hello All!

I have a very basic problem:

My computer is attached to various light switches, central heating, powered windows etc. via RS232 and USB, using homemade custom logic boards.

With this I can switch on and off lights, regulate room temperature, open windows etc. all by running some shell scripts on my system.

I would now like to create a simple web frontend for this home automation.

What I want is a basic website with buttons, and when someone clicks a button on that website I want the webserver (apache ? ) to execute a script on the the server machine, triggering the rs232 hardware.

The website is to be served by apache to make use of an existing structure.


How (in what language) could I accomplish that? Javascript and Java are obviously out since they execute on the client, as far as I know PHP can't access the shell (which is probably a good thing), so what's left?

CGI?

This will be deployed on an isolated private network secured the old-fashioned way (steel doors, guard dogs, landmines...), so I am not overly concerned about security, but of course it would be nice if the implementation offered at least some basic resistance to bored script kiddies...

Does anyone have an example I could look at?

---

### Post by Sam Goodspeed on 2011-08-25
never mind, PHP can do it via the exec functions. It's been a while...

---

### Post by SeijiSensei on 2011-08-25
PHP can certainly run shell commands, though they will be running as the www-data user.  That's the user the Apache webserver runs under.  PHP even includes the "backtick" operator used in *nix shells.  For more details, see this section on "[program execution]("http://www.php.net/manual/en/ref.exec.php")" in the PHP manual.

If you need direct root access, you're out of luck.  One kludge is to use PHP to queue up commands in a specified directory to which the www-data user has file-creation rights.  Then a shell script runs periodically from root's crontab, checks the queue, and executes the commands it finds.

If you don't need root access, just make sure your scripts are executable by the www-data user.

---

### Post by Sam Goodspeed on 2011-08-25
Thanks for the clarification.

I think I can manage with wwwdata.

it just needs write access to the respective RS232 ports then, but that I can accomplish by just manually adding the user to the respective system groups, so exec() should do the trick for me.

---

