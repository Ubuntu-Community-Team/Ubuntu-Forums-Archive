---
title: "libxmlrpc-c3-dev broken in natty?"
date: 2011-05-08
forum: Server Platforms
---

### Post by jobsonandrew on 2011-05-08
Hi,
I need a xmlrpc client on 11.04 server edition that I can use in shell scripts and the like.. so I installed this:
```
sudo apt-get install libxmlrpc-c3-dev
```
which installed all its dependencies too of course:
```
The following NEW packages will be installed:
  libxmlrpc-c3-0 libxmlrpc-c3-dev libxmlrpc-core-c3-0 libxmlrpc-core-c3-dev

```
However, when I try to use the client in any way (with or without any command line parameters, I get this:
```
andy@pandora:~$ xmlrpc
xmlrpc: symbol lookup error: /usr/lib/libxmlrpc_client.so.3: undefined symbol: xmlrpc_strsol

```
shouldn't this just work? it worked in Debian squeeze and earlier versions of Ubuntu.. does it work for you? what can I do to resolve the problem?

---

### Post by jobsonandrew on 2011-06-30
I wasn't able to fix this but I was able to work around it with Perl.

All I wanted was to use a script to determine the number of active torrents (downloading/seeding) in rTorrent.

Using xmlrpc I would have done this:
```
xmlrpc localhost download_list active
```

but due to problems explained in the OP, this didn't work.

The same thing can be achieved with Perl:
```
#!/usr/bin/perl

require RPC::XML;
require RPC::XML::Client;

use strict;

my $cli;
my $resp;

$cli = RPC::XML::Client->new('http://localhost/RPC2');

$resp = $cli->send_request(RPC::XML::request->new('download_list','active'));

print scalar(grep {defined $_} @{$resp->value});

```
This script returns the number of active torrents in rTorrent (note the server string if you want to use it)

Also, rTorrent needs to be compiled from source with XML-RPC support (google how to do this).. the rtorrent version in the repositories doesn't support XML-RPC

Cheers!

---

