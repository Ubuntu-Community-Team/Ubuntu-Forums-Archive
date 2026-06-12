---
title: "Microstack Multinode"
date: 2022-06-02
forum: Server Platforms
---

### Post by quentindixon on 2022-06-02
Having issues adding node to control. Everything is setup remotely using production servers. Servers have 2 nics all initialized and resolving remotely. Installs were simple with no errors. Both control and node has recent updates. PROBLEM: can not add nodes to control... copy and paste below:

[COLOR=#000000][FONT=Menlo][COLOR=#2fb41d]**aeiia@node1**[/COLOR]:[COLOR=#400bd9]**~**[/COLOR]$ sudo microstack init[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][sudo] password for aeiia: [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Would you like to configure clustering? (yes/no) [default=yes] > yes[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]2022-06-02 13:49:44,101 - microstack_init - INFO - Configuring clustering ...[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Which role would you like to use for this node: "control" or "compute"? > compute[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Please enter the ip address of this node [default=104.219.12.33] > 104.219.12.33[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Please enter a connection string returned by the add-compute command >  [default=hKhob3N0bmFtZa0xMDQuMjE5LjEyLjMxq2ZpbmdlcnByaW50xCBW5DDVwl7pghkT5PzoIPWAJOXgGN+PYwVVj+PxUCPdcKJpZNkgNjcxZmZhZmRlNGEyNDQ0MjlhZjk5NjExMmIzYWFmNTmmc2VjcmV02SB5QVFqV3FPcHFSQVc3SERoYnpMYjFjMnc4d3dkRjRmNw==] > hKhob3N0bmFtZa0xMDQuMjE5LjEyLjMxq2ZpbmdlcnByaW50xCBW5DDVwl7pghkT5PzoIPWAJOXgGN+PYwVVj+PxUCPdcKJpZNkgOGEyYzQ0NGUwNDNiNGNiN2FmMWIwZjIzMzM2OTQ0NzKmc2VjcmV02SBCWHVFRy1ROGJYX3VKVm82a3RTMEdCUEV5aENaNy1NZw==[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]2022-06-02 13:50:26,580 - microstack_init - INFO - Setting up as a compute node.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Traceback (most recent call last):[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]  File "/snap/microstack/245/bin/microstack_join", line 11, in <module>[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]    load_entry_point('microstack-cluster==0.0.1', 'console_scripts', 'microstack_join')()[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]  File "/snap/microstack/245/lib/python3.8/site-packages/cluster/client.py", line 79, in join[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]    raise UnauthorizedRequestError(message)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]cluster.client.UnauthorizedRequestError: b'<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 3.2 Final//EN">\n<title>500 Internal Server Error</title>\n<h1>Internal Server Error</h1>\n<p>The server encountered an internal error and was unable to complete your request. Either the server is overloaded or there is an error in the application.</p>\n'[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Traceback (most recent call last):[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]  File "/snap/microstack/245/bin/microstack", line 11, in <module>[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]    load_entry_point('microstack==0.0.1', 'console_scripts', 'microstack')()[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]  File "/snap/microstack/245/lib/python3.8/site-packages/microstack/main.py", line 44, in main[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]    cmd()[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]  File "/snap/microstack/245/lib/python3.8/site-packages/init/main.py", line 60, in wrapper[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]    return func(*args, **kwargs)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]  File "/snap/microstack/245/lib/python3.8/site-packages/init/main.py", line 228, in init[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]    question.ask()[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]  File "/snap/microstack/245/lib/python3.8/site-packages/init/questions/question.py", line 210, in ask[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]    self.yes(awr)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]  File "/snap/microstack/245/lib/python3.8/site-packages/init/questions/__init__.py", line 105, in yes[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]    check_output('microstack_join')[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]  File "/snap/microstack/245/lib/python3.8/site-packages/init/shell.py", line 81, in check_output[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]    return subprocess.check_output(args, env=env,[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]  File "/usr/lib/python3.8/subprocess.py", line 415, in check_output[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]    return run(*popenargs, stdout=PIPE, timeout=timeout, check=True,[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]  File "/usr/lib/python3.8/subprocess.py", line 516, in run[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]    raise CalledProcessError(retcode, process.args,[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]subprocess.CalledProcessError: Command '('microstack_join',)' returned non-zero exit status 1.[/FONT][/COLOR]
[COLOR=#2FB41D][FONT=Menlo]**aeiia@node1**[COLOR=#000000]:[/COLOR][COLOR=#400bd9]**~**[/COLOR][COLOR=#000000]$[/COLOR][/FONT][/COLOR]

---

### Post by quentindixon on 2022-06-02
Fixed.

Forced updates on all packages on Control and Compute:
[COLOR=#000000][FONT=Monaco]
apt list [/FONT][/COLOR][COLOR=#000000][FONT=Monaco]--upgradable
[COLOR=#2060A0]sudo[/COLOR] apt upgrade
apt list --upgradable (verify all updates)

Reinitialized both Control and Compute (had to do this a couple times):

sudo systemctl restart snap.microstack.*
Note: seems like the microstack is not smart enough to reinitialize after an add compute command. Might be a bug...

[/FONT][/COLOR]

---

### Post by #&amp;thj^% on 2022-06-02
So is this method broken?
```
sudo microstack.init --auto
```
I'm guessing right now but the path should be in:
```
PATH=/snap/bin:$PATH /snap/bin/microstack.init --auto --control

```

---

