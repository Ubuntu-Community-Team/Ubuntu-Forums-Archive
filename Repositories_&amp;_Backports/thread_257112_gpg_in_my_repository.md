---
title: "gpg in my repository"
date: 2006-09-14
forum: Repositories &amp; Backports
---

### Post by jsgaarde on 2006-09-14
Hi.

I am trying to create my own deb repository. So far I have the the repository working but I am not using gpg. I am new to gpg and need some pointers to get started. 

[OK] 1. I have the repository (unsigned, using dpkg-deb and dpkg-scanpackages)
[OK] 2. I have created a gpg key (gpg --gen-key)
[??] 3. What needs to be signed and how? When I look at the ubuntu repositories it I can see there is a Release/Release.gpg set under each distribution. This files appear to have been generated but how?
[??] 4. Do I need to sign anything else? I can see som .dsc files in some of the pool directories, but it doesn't seem like all packages have one.

Thanks
Jakob

---

### Post by jamadagni on 2006-09-14
1. Create a Release file using your favourite text editor after the pattern of the Release files you see in the official repos.

2. Use md5 to create the md5sums. I don't know about shasums.

3. Now use gpg -bao Release.gpg Release to create the Release.gpg file. 

4. Then export your public key which you used in the previous step.

5. Import that key to apt using apt-key add <keyfilename>

---

### Post by jsgaarde on 2006-09-17
Thanks jamadagni, that helped me the last step :)

I have one odd problem yet though: 
I have calculated the md5sums and sha1sums and put the distribution on my server. When I then test the repository I get a md5sum Mismatch error on the binary-i386/Packages.bz2 file. The odd thing about this is that the md5sum is correct in the repository. I have solved this problem until now by removing that specific file so that only the Packages and Packages.gz files are in that architechture.

I have written a pythonscript to produce a full distribution based on a folder of .deb-files.

Your need the following two scripts "build-apt" and "Release_template":
build-apt:
```
#!/usr/bin/python

import sys,md5,sha,os
from optparse import OptionParser

usage = "Usage: create_repository suite"
parser = OptionParser(usage=usage)

md5list = []
sha1list = []

if __name__=='__main__':

        (options, args) = parser.parse_args()

        if len(args)==0:
                suite = raw_input("Which suite is to be build: ")
        else:
                suite = args[0]

        # Load debinfo
        if not os.path.exists('%s_aptinfo.py' % suite):
                print "ERROR: %s_aptinfo.py is missing" % suite
                sys.exit(0)
        aptinfo = __import__('%s_aptinfo' % suite)

        # Clean workspaces
        if os.path.exists('dists'):
                os.system('sudo rm dists -R -f')
        os.makedirs('dists/%s' % suite)

        if os.path.exists('pool'):
                os.system('sudo rm pool -R -f')

        component_list = os.listdir(suite)
        arch_list = []
        for component in component_list:
                if os.path.isdir('%s/%s' % (suite,component)):
                        component_archs = os.listdir('%s/%s' % (suite,component))
                        for arch in component_archs:
                                if not arch_list.count(arch) and \
                                   os.path.isdir('%s/%s/%s' % (suite,component,arch)):
                                        arch_list += [arch]
                else:
                        component_list.pop(component)

        for component in component_list:
                for arch in arch_list:
                        if not os.path.exists('%s/%s/%s' % (suite,component,arch)):
                                # this component did not contain specific packages for that architechture
                                continue
                        os.system('sudo rm pool -R -f')
                        os.mkdir('pool')
                        os.system("ln -s ../%s/%s/%s pool/%s " % (suite,component,arch,component))

                        if not os.path.exists('real_pool/%s' % component):
                                os.makedirs('real_pool/%s' % component)
                        os.system("cp %s/%s/%s/* real_pool/%s -Rfv" % (suite,component,arch,component))
                        if arch=='source':
                                dist_packages_dir = 'dists/%s/%s/%s' % (suite,component,arch)
                                os.makedirs(dist_packages_dir)
                                os.system('sudo dpkg-scansources pool/%s /dev/null > %s/Sources' % (component,dist_source_dir))
                                os.system('tar cjf %s/Sources.bz2 %s/Sources' % (dist_source_dir,dist_source_dir))
                                os.system('gzip -9c %s/Sources > %s/Sources.gz' % (dist_source_dir,dist_source_dir))
                        else:
                                dist_binary_dir = 'dists/%s/%s/binary-%s' % (suite,component,arch)
                                os.makedirs(dist_binary_dir)
                                os.system('sudo dpkg-scanpackages pool/%s /dev/null > %s/Packages' % (component,dist_binary_dir))
                                os.system('tar cjf %s/Packages.bz2 %s/Packages' % (dist_binary_dir,dist_binary_dir))
                                os.system('gzip -9c %s/Packages > %s/Packages.gz' % (dist_binary_dir,dist_binary_dir))

        os.system('sudo rm pool -R -f')
        os.system('sudo mv real_pool pool')

        f = open('Release_template')
        buf = f.read()
        f.close()

        for tag in aptinfo.release_info.keys():
                buf = buf.replace('<%s>' % tag, aptinfo.release_info[tag])
        buf = buf.replace('<components>',' '.join(component_list))
        buf = buf.replace('<architechtures>',' '.join(arch_list))

        def digest(args,dirname,fnames):
                global md5list,sha1list
                for fn in fnames:
                        if os.path.isdir(os.path.join(dirname,fn)):
                                continue
                        fsize = os.path.getsize(os.path.join(dirname,fn))
                        f = open(os.path.join(dirname,fn))
                        bytes=f.read()
                        md5sum = md5.md5(bytes).hexdigest()
                        sha1 = sha.sha(bytes).hexdigest()
                        f.close()
                        del bytes
                        md5list += [' %s%17.17s %s' % (md5sum,fsize,os.path.sep.join(os.path.join(dirname,fn).split(os.path.sep)[2:]))]
                        sha1list += [' %s%17.17s %s' % (sha1,fsize,os.path.sep.join(os.path.join(dirname,fn).split(os.path.sep)[2:]))]

        os.path.walk('dists/%s' % suite,digest,None)

        buf = buf.replace('<md5sum>','\n'.join(md5list))
        buf = buf.replace('<sha1>','\n'.join(sha1list))

        f = open('dists/%s/Release' % suite, 'w')
        f.write(buf)
        f.close()
        os.system('gpg -abs -o dists/%s/Release.gpg dists/%s/Release' % (suite,suite))

```

Release_template:
```
Origin: <origin>
Label: <label>
Suite: <suite>
Version: <version>
Codename: <codename>
Architectures: <architechtures>
Components: <components>
Description: <description>
MD5Sum:
<md5sum>
SHA1:
<sha1>
```

Also you need a private gpg key for signing the Release file. You can create one like this:
```
gpg --gen-key
```

1. Create the distribution hierarchi:
example: (the distribution "pilot")
```
pilot
pilot/main
pilot/main/i386
pilot/main/i386/python2.4-skolesys_0.5-skolesys1_all.deb
pilot/main/i386/skolesys-ltsp_4.2-2-skolesys1_i386.deb
pilot/main/amd64
pilot/main/amd64/python2.4-skolesys_0.5-skolesys1_all.deb
pilot/nonfree
pilot/nonfree/i386
pilot/nonfree/i386/skolesys-ui_0.5.1-skolesys1_all.deb
pilot/nonfree/amd64
pilot/nonfree/amd64/skolesys-ui_0.5.1-skolesys1_all.deb
```

2. Create a aptinfo file for the distribution
pilot_aptinfo:
```
release_info = {
        'origin': 'SkoleSYS',
        'label': 'SkoleSYS',
        'suite': 'pilot',
        'version': '0.51',
        'codename': 'pilot',
        'description': 'SkoleSYS Pilot 0.51'}
```

3. Run the apt-repository builder:
```
./build-apt pilot
```

4. Copy the folders dists and pool to your apt location of your webserver.

---

