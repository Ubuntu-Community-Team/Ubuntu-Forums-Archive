---
title: "Help please: cant get sinopia installed on 14.04 server"
date: 2015-09-04
forum: Server Platforms
---

### Post by bill86 on 2015-09-04
Hi all, I've spend about a week scrummaging through google links on how to get a private npm up and running. Went though NPM-e, sort of almost worked, had authentication issues when not connected externally, gave up and decided to try something simpler. SO I landed on sinopia, seemed to fit the bill by everyone's descriptions.

So here I am: I've followed every set of instructions I can find and still have no luck. I figure maybe someone here has been through this already and can help me out, I want to give sinopia one last shot before writing it off on ubuntu.

-First I followed these instructions: [https://www.npmjs.com/package/sinopia](https://www.npmjs.com/package/sinopia) and had no luck, then I tried all kinds of installations for the dependancies, ended up in big loops of make this work before that, but that has to work before another, which doesn't work with some version because something has a bug everyone knows about, etc...
-I tried this: [https://blog.dylants.com/2014/05/10/creating-a-private-npm-registry-with-sinopia/](https://blog.dylants.com/2014/05/10/creating-a-private-npm-registry-with-sinopia/) and think that's way too simplified and misses about 90% of what you need beforehand, so I gave up after a few rounds there.
-I tried this: [http://thejackalofjavascript.com/maintaining-a-private-npm-registry/](http://thejackalofjavascript.com/maintaining-a-private-npm-registry/) more of the same issues with the previous instructions...


Basically, I want my developers to have a local npm to share private json packages internally but this is getting crazy.

---

### Post by PaulW2U on 2015-09-04
*Thread moved to **Server Platforms**.*

Moving here as it's probably a better place for your rather specialised issue.

---

### Post by bill86 on 2015-09-08
Thanks PaulW2U.

I just rebuilt my server from scratch. This is my default server install process (VMware ESXi vm):

> 
sudo mkdir -p /media/cdrom
sudo mount /dev/cdrom /media/cdrom
cd /media/cdrom
sudo cp VM*.tar.gz /tmp
sudo apt-get -y install linux-headers-server build-essential
cd /tmp
sudo umount /media/cdrom
sudo tar xzvf VM*.tar.gz
cd vmware-tools-distrib
sudo mkdir -p /usr/lib/vmware-tools
sudo mkdir -p /usr/share/doc/vmware-tools
sudo ./vmware-install.pl -q
sudo reboot
-------------------------
sudo apt-get install curl
curl -sL [https://deb.nodesource.com/setup_0.12](https://deb.nodesource.com/setup_0.12) | sudo bash -
sudo apt-get install nodejs


Now, when I try to install sinopia without sudo (as shown in the instructions here: [https://www.npmjs.com/package/sinopia](https://www.npmjs.com/package/sinopia) ) this is the result I get:


> 
[EMAIL="administrator@sinopia:~$"]administrator@sinopia:~$[/EMAIL] npm install -g sinopia
npm ERR! tar.unpack untar error /home/administrator/.npm/sinopia/1.4.0/package.t            gz
npm ERR! Linux 3.16.0-30-generic
npm ERR! argv "/usr/bin/node" "/usr/bin/npm" "install" "-g" "sinopia"
npm ERR! node v0.12.7
npm ERR! npm  v2.11.3
npm ERR! path /usr/lib/node_modules/sinopia
npm ERR! code EACCES
npm ERR! errno -13
npm ERR! Error: EACCES, mkdir '/usr/lib/node_modules/sinopia'
npm ERR!     at Error (native)
npm ERR!  { [Error: EACCES, mkdir '/usr/lib/node_modules/sinopia']
npm ERR!   errno: -13,
npm ERR!   code: 'EACCES',
npm ERR!   path: '/usr/lib/node_modules/sinopia',
npm ERR!   fstream_type: 'Directory',
npm ERR!   fstream_path: '/usr/lib/node_modules/sinopia',
npm ERR!   fstream_class: 'DirWriter',
npm ERR!   fstream_stack:
npm ERR!    [ '/usr/lib/node_modules/npm/node_modules/fstream/lib/dir-writer.js:            35:25',
npm ERR!      '/usr/lib/node_modules/npm/node_modules/mkdirp/index.js:47:53',
npm ERR!      'FSReqWrap.oncomplete (fs.js:95:15)' ] }
npm ERR!
npm ERR! Please try running this command again as root/Administrator.
npm ERR! Please include the following file with any support request:
npm ERR!     /home/administrator/npm-debug.log
administrator@sinopia:~$



So, I tried with sudo and I get file permissions errors to paths that do not exist. IE:

> 
administrator@sinopia:~$ sudo npm install -g sinopia
> [EMAIL="crypt3@0.1.8"]crypt3@0.1.8[/EMAIL] install /usr/lib/node_modules/sinopia/node_modules/crypt3
> node-gyp rebuild
gyp WARN EACCES user "root" does not have permission to access the dev dir "/home/administrator/.node-gyp/0.12.7"
gyp WARN EACCES attempting to reinstall using temporary dev dir "/usr/lib/node_modules/sinopia/node_modules/crypt3/.node-gyp"
make: Entering directory `/usr/lib/node_modules/sinopia/node_modules/crypt3/build'
  CXX(target) Release/obj.target/crypt3/crypt3.o
  SOLINK_MODULE(target) Release/obj.target/crypt3.node
  COPY Release/crypt3.node
make: Leaving directory `/usr/lib/node_modules/sinopia/node_modules/crypt3/build'
> [EMAIL="fs-ext@0.4.5"]fs-ext@0.4.5[/EMAIL] install /usr/lib/node_modules/sinopia/node_modules/fs-ext
> node-gyp configure build
gyp WARN EACCES user "root" does not have permission to access the dev dir "/home/administrator/.node-gyp/0.12.7"
gyp WARN EACCES attempting to reinstall using temporary dev dir "/usr/lib/node_modules/sinopia/node_modules/fs-ext/.node-gyp"
make: Entering directory `/usr/lib/node_modules/sinopia/node_modules/fs-ext/build'
  CXX(target) Release/obj.target/fs-ext/fs-ext.o
  SOLINK_MODULE(target) Release/obj.target/fs-ext.node
  COPY Release/fs-ext.node
make: Leaving directory `/usr/lib/node_modules/sinopia/node_modules/fs-ext/build'
> [EMAIL="dtrace-provider@0.4.0"]dtrace-provider@0.4.0[/EMAIL] install /usr/lib/node_modules/sinopia/node_modules/bunyan/node_modules/dtrace-provider
> node scripts/install.js
/usr/bin/sinopia -> /usr/lib/node_modules/sinopia/bin/sinopia
[EMAIL="sinopia@1.4.0"]sinopia@1.4.0[/EMAIL] /usr/lib/node_modules/sinopia
âââ [EMAIL="sinopia-htpasswd@0.4.5"]sinopia-htpasswd@0.4.5[/EMAIL]
âââ [EMAIL="async@0.9.2"]async@0.9.2[/EMAIL]
âââ [EMAIL="http-errors@1.3.1"]http-errors@1.3.1[/EMAIL] ([EMAIL="inherits@2.0.1"]inherits@2.0.1[/EMAIL], [EMAIL="statuses@1.2.1"]statuses@1.2.1[/EMAIL])
âââ [EMAIL="cookies@0.5.0"]cookies@0.5.0[/EMAIL] ([EMAIL="keygrip@1.0.1"]keygrip@1.0.1[/EMAIL])
âââ [EMAIL="commander@2.8.1"]commander@2.8.1[/EMAIL] ([EMAIL="graceful-readlink@1.0.1"]graceful-readlink@1.0.1[/EMAIL])
âââ [EMAIL="es6-shim@0.21.1"]es6-shim@0.21.1[/EMAIL]
âââ [EMAIL="jju@1.2.0"]jju@1.2.0[/EMAIL]
âââ [EMAIL="minimatch@1.0.0"]minimatch@1.0.0[/EMAIL] ([EMAIL="sigmund@1.0.1"]sigmund@1.0.1[/EMAIL], [EMAIL="lru-cache@2.6.4"]lru-cache@2.6.4[/EMAIL])
âââ [EMAIL="readable-stream@1.1.13"]readable-stream@1.1.13[/EMAIL] ([EMAIL="inherits@2.0.1"]inherits@2.0.1[/EMAIL], [EMAIL="isarray@0.0.1"]isarray@0.0.1[/EMAIL], [EMAIL="string_decoder@0.10.31"]string_decoder@0.10.31[/EMAIL], [EMAIL="core-util-is@1.0.1"]core-util-is@1.0.1[/EMAIL])
âââ [EMAIL="mkdirp@0.5.1"]mkdirp@0.5.1[/EMAIL] ([EMAIL="minimist@0.0.8"]minimist@0.0.8[/EMAIL])
âââ [EMAIL="compression@1.4.4"]compression@1.4.4[/EMAIL] ([EMAIL="vary@1.0.0"]vary@1.0.0[/EMAIL], [EMAIL="on-headers@1.0.0"]on-headers@1.0.0[/EMAIL], [EMAIL="bytes@1.0.0"]bytes@1.0.0[/EMAIL], [EMAIL="debug@2.2.0"]debug@2.2.0[/EMAIL], [EMAIL="compressible@2.0.2"]compressible@2.0.2[/EMAIL], [EMAIL="accepts@1.2.7"]accepts@1.2.7[/EMAIL])
âââ express@5.0.0-alpha.1 ([EMAIL="vary@1.0.0"]vary@1.0.0[/EMAIL], [EMAIL="merge-descriptors@0.0.2"]merge-descriptors@0.0.2[/EMAIL], [EMAIL="utils-merge@1.0.0"]utils-merge@1.0.0[/EMAIL], [EMAIL="fresh@0.2.4"]fresh@0.2.4[/EMAIL], [EMAIL="cookie@0.1.2"]cookie@0.1.2[/EMAIL], [EMAIL="escape-html@1.0.1"]escape-html@1.0.1[/EMAIL], [EMAIL="range-parser@1.0.2"]range-parser@1.0.2[/EMAIL], [EMAIL="cookie-signature@1.0.5"]cookie-signature@1.0.5[/EMAIL], [EMAIL="finalhandler@0.3.2"]finalhandler@0.3.2[/EMAIL], [EMAIL="media-typer@0.3.0"]media-typer@0.3.0[/EMAIL], [EMAIL="parseurl@1.3.0"]parseurl@1.3.0[/EMAIL], [EMAIL="methods@1.1.0"]methods@1.1.0[/EMAIL], [EMAIL="serve-static@1.7.2"]serve-static@1.7.2[/EMAIL], [EMAIL="content-disposition@0.5.0"]content-disposition@0.5.0[/EMAIL], [EMAIL="path-to-regexp@0.1.3"]path-to-regexp@0.1.3[/EMAIL], [EMAIL="depd@1.0.1"]depd@1.0.1[/EMAIL], [EMAIL="on-finished@2.1.1"]on-finished@2.1.1[/EMAIL], [EMAIL="qs@2.3.2"]qs@2.3.2[/EMAIL], [EMAIL="debug@2.1.3"]debug@2.1.3[/EMAIL], [EMAIL="etag@1.5.1"]etag@1.5.1[/EMAIL], [EMAIL="proxy-addr@1.0.8"]proxy-addr@1.0.8[/EMAIL], [EMAIL="send@0.10.1"]send@0.10.1[/EMAIL], [EMAIL="type-is@1.5.7"]type-is@1.5.7[/EMAIL], [EMAIL="accepts@1.1.4"]accepts@1.1.4[/EMAIL])
âââ [EMAIL="body-parser@1.12.4"]body-parser@1.12.4[/EMAIL] ([EMAIL="bytes@1.0.0"]bytes@1.0.0[/EMAIL], [EMAIL="content-type@1.0.1"]content-type@1.0.1[/EMAIL], [EMAIL="depd@1.0.1"]depd@1.0.1[/EMAIL], [EMAIL="qs@2.4.2"]qs@2.4.2[/EMAIL], [EMAIL="raw-body@2.0.2"]raw-body@2.0.2[/EMAIL], [EMAIL="on-finished@2.2.1"]on-finished@2.2.1[/EMAIL], [EMAIL="debug@2.2.0"]debug@2.2.0[/EMAIL], [EMAIL="type-is@1.6.2"]type-is@1.6.2[/EMAIL], [EMAIL="iconv-lite@0.4.8"]iconv-lite@0.4.8[/EMAIL])
âââ [EMAIL="JSONStream@1.0.3"]JSONStream@1.0.3[/EMAIL] ([EMAIL="through@2.3.7"]through@2.3.7[/EMAIL], [EMAIL="jsonparse@1.0.0"]jsonparse@1.0.0[/EMAIL])
âââ [EMAIL="express-json5@0.1.0"]express-json5@0.1.0[/EMAIL] ([EMAIL="raw-body@1.3.4"]raw-body@1.3.4[/EMAIL])
âââ [EMAIL="request@2.56.0"]request@2.56.0[/EMAIL] ([EMAIL="caseless@0.10.0"]caseless@0.10.0[/EMAIL], [EMAIL="aws-sign2@0.5.0"]aws-sign2@0.5.0[/EMAIL], [EMAIL="stringstream@0.0.4"]stringstream@0.0.4[/EMAIL], [EMAIL="forever-agent@0.6.1"]forever-agent@0.6.1[/EMAIL], [EMAIL="tunnel-agent@0.4.0"]tunnel-agent@0.4.0[/EMAIL], [EMAIL="oauth-sign@0.8.0"]oauth-sign@0.8.0[/EMAIL], [EMAIL="isstream@0.1.2"]isstream@0.1.2[/EMAIL], [EMAIL="json-stringify-safe@5.0.1"]json-stringify-safe@5.0.1[/EMAIL], [EMAIL="node-uuid@1.4.3"]node-uuid@1.4.3[/EMAIL], [EMAIL="qs@3.1.0"]qs@3.1.0[/EMAIL], [EMAIL="combined-stream@1.0.3"]combined-stream@1.0.3[/EMAIL], [EMAIL="mime-types@2.0.12"]mime-types@2.0.12[/EMAIL], [EMAIL="form-data@0.2.0"]form-data@0.2.0[/EMAIL], [EMAIL="bl@0.9.4"]bl@0.9.4[/EMAIL], [EMAIL="http-signature@0.11.0"]http-signature@0.11.0[/EMAIL], [EMAIL="tough-cookie@1.2.0"]tough-cookie@1.2.0[/EMAIL], [EMAIL="hawk@2.3.1"]hawk@2.3.1[/EMAIL], [EMAIL="har-validator@1.7.1"]har-validator@1.7.1[/EMAIL])
âââ [EMAIL="highlight.js@8.6.0"]highlight.js@8.6.0[/EMAIL]
âââ [EMAIL="semver@4.3.5"]semver@4.3.5[/EMAIL]
âââ [EMAIL="lunr@0.5.9"]lunr@0.5.9[/EMAIL]
âââ [EMAIL="js-yaml@3.3.1"]js-yaml@3.3.1[/EMAIL] ([EMAIL="esprima@2.2.0"]esprima@2.2.0[/EMAIL], [EMAIL="argparse@1.0.2"]argparse@1.0.2[/EMAIL])
âââ [EMAIL="render-readme@1.3.0"]render-readme@1.3.0[/EMAIL] ([EMAIL="sanitize-html@1.6.1"]sanitize-html@1.6.1[/EMAIL], [EMAIL="markdown-it@4.2.1"]markdown-it@4.2.1[/EMAIL])
âââ [EMAIL="handlebars@2.0.0"]handlebars@2.0.0[/EMAIL] ([EMAIL="optimist@0.3.7"]optimist@0.3.7[/EMAIL], [EMAIL="uglify-js@2.3.6"]uglify-js@2.3.6[/EMAIL])
âââ [EMAIL="crypt3@0.1.8"]crypt3@0.1.8[/EMAIL] ([EMAIL="nan@1.8.4"]nan@1.8.4[/EMAIL])
âââ [EMAIL="fs-ext@0.4.5"]fs-ext@0.4.5[/EMAIL] ([EMAIL="nan@1.8.4"]nan@1.8.4[/EMAIL])
âââ [EMAIL="bunyan@1.3.5"]bunyan@1.3.5[/EMAIL] ([EMAIL="safe-json-stringify@1.0.3"]safe-json-stringify@1.0.3[/EMAIL], [EMAIL="mv@2.0.3"]mv@2.0.3[/EMAIL], [EMAIL="dtrace-provider@0.4.0"]dtrace-provider@0.4.0[/EMAIL])
administrator@sinopia:~$


It actually installs but does not function (I get warnings for config.yaml and http address returned when I run 'sinopia', instead of the expected configuration options screens )

---

### Post by bill86 on 2015-09-08
Figured it out....no idea why build-essential doesn't include such silly things like tools like autoconf and automake, which are needed for almost any type of development.

Trial and error have shown this is all that was missing from the above:

sudo apt-get install automake autoconf

---

### Post by Habitual on 2015-09-08
Good job and well done!

---

