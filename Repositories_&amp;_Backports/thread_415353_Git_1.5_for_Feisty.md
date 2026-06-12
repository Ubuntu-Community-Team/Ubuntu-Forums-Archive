---
title: "Git 1.5 for Feisty"
date: 2007-04-20
forum: Repositories &amp; Backports
---

### Post by gummibaerchen on 2007-04-20
Hi,

I am searching like mad for a git package for Feisty as it doesn't build for me the way I want.

Anyone?

:guitar:

---

### Post by exidez on 2007-04-30
i also need the same
i cant install the git package from [http://www.kernel.org/pub/software/scm/git/](http://www.kernel.org/pub/software/scm/git/)
the current version i have is 1.4.4.2 but i need the latest as it is still buggy

can anyone help
when making i get this error
$ make
/bin/sh: curl-config: not found
    CC convert-objects.o
In file included from convert-objects.c:1:
cache.h:6:21: error: openssl/sha.h: No such file or directory
cache.h:7:18: error: zlib.h: No such file or directory
make: *** [convert-objects.o] Error 1

---

### Post by jackbravo on 2007-05-02
> **exidez said:**
> $ make
/bin/sh: curl-config: not found
    CC convert-objects.o
In file included from convert-objects.c:1:
cache.h:6:21: error: openssl/sha.h: No such file or directory
cache.h:7:18: error: zlib.h: No such file or directory
make: *** [convert-objects.o] Error 1

Had the exact same error...
I installed the packages: build-essential, libcurl3-dev, zlib1g-dev and libssl-dev
but then this error appeared:

```
    LINK git-ssh-push
    CC http.o
    CC http-fetch.o
    LINK git-http-fetch
/usr/bin/ld: cannot find -lexpat
collect2: ld returned 1 exit status
make: *** [git-http-fetch] Error 1
```

---

### Post by jackbravo on 2007-05-02
seems I was missing libexpat1-dev too.
now make was succesfull =)

---

### Post by exidez on 2007-05-02
i kind of get this problem.... ???


$ make install
    SUBDIR git-gui
make[1]: Nothing to be done for `all'.
    SUBDIR perl
    SUBDIR templates
install -d -m755 '/home/exidez/bin'
install -d -m755 '/home/exidez/bin'
install git-convert-objects git-fetch-pack git-fsck git-hash-object git-index-pack git-local-fetch git-fast-import git-merge-base git-daemon git-merge-index git-mktag git-mktree git-patch-id git-peek-remote git-receive-pack git-send-pack git-shell git-show-index git-ssh-fetch git-ssh-upload git-unpack-file git-update-server-info git-upload-pack git-verify-pack git-pack-redundant git-var git-merge-tree git-imap-send git-merge-recursive  git-ssh-pull git-ssh-push git-http-fetch git-http-push git-bisect git-checkout git-clean git-clone git-commit git-fetch git-ls-remote git-merge-one-file git-mergetool git-parse-remote git-pull git-rebase git-repack git-request-pull git-reset git-sh-setup git-tag git-verify-tag git-applymbox git-applypatch git-am git-merge git-merge-stupid git-merge-octopus git-merge-resolve git-merge-ours git-lost-found git-quiltimport git-add--interactive git-archimport git-cvsimport git-relink git-cvsserver git-remote git-svnimport git-cvsexportcommit git-send-email git-svn git-status git-instaweb '/home/exidez/bin'
install git gitk '/home/exidez/bin'
make -C templates DESTDIR='' install
make[1]: Entering directory `/home/exidez/git-1.5.1/templates'
install -d -m755 '/home/exidez/share/git-core/templates/'
(cd blt && tar cf - .) | \
        (cd '/home/exidez/share/git-core/templates/' && tar xf -)
make[1]: Leaving directory `/home/exidez/git-1.5.1/templates'
make -C perl prefix='/home/exidez' install
make[1]: Entering directory `/home/exidez/git-1.5.1/perl'
make[2]: Entering directory `/home/exidez/git-1.5.1/perl'
Writing /home/exidez/lib/perl/5.8.8/auto/Git/.packlist
Appending installation info to /home/exidez/lib/perl/5.8.8/perllocal.pod
make[2]: Leaving directory `/home/exidez/git-1.5.1/perl'
make[1]: Leaving directory `/home/exidez/git-1.5.1/perl'
make -C git-gui install
make[1]: Entering directory `/home/exidez/git-1.5.1/git-gui'
install -d -m755 '/home/exidez/bin'
install git-gui '/home/exidez/bin'
rm -f '/home/exidez/bin/git-citool' && ln '/home/exidez/bin/git-gui' '/home/exidez/bin/git-citool' ;
make[1]: Leaving directory `/home/exidez/git-1.5.1/git-gui'
if test 'z/home/exidez/bin' != 'z/home/exidez/bin'; \
        then \
                ln -f '/home/exidez/bin/git' \
                        '/home/exidez/bin/git' || \
                cp '/home/exidez/bin/git' \
                        '/home/exidez/bin/git'; \
        fi
rm -f '/home/exidez/bin/git-format-patch' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-format-patch' ;  rm -f '/home/exidez/bin/git-show' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-show' ;  rm -f '/home/exidez/bin/git-whatchanged' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-whatchanged' ;  rm -f '/home/exidez/bin/git-cherry' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-cherry' ;  rm -f '/home/exidez/bin/git-get-tar-commit-id' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-get-tar-commit-id' ;  rm -f '/home/exidez/bin/git-init' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-init' ;  rm -f '/home/exidez/bin/git-repo-config' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-repo-config' ;  rm -f '/home/exidez/bin/git-fsck-objects' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-fsck-objects' ;  rm -f '/home/exidez/bin/git-cherry-pick' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-cherry-pick' ;  rm -f '/home/exidez/bin/git-add' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-add' ;  rm -f '/home/exidez/bin/git-annotate' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-annotate' ;  rm -f '/home/exidez/bin/git-apply' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-apply' ;  rm -f '/home/exidez/bin/git-archive' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-archive' ;  rm -f '/home/exidez/bin/git-blame' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-blame' ;  rm -f '/home/exidez/bin/git-branch' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-branch' ;  rm -f '/home/exidez/bin/git-bundle' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-bundle' ;  rm -f '/home/exidez/bin/git-cat-file' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-cat-file' ;  rm -f '/home/exidez/bin/git-checkout-index' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-checkout-index' ;  rm -f '/home/exidez/bin/git-check-ref-format' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-check-ref-format' ;  rm -f '/home/exidez/bin/git-commit-tree' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-commit-tree' ;  rm -f '/home/exidez/bin/git-count-objects' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-count-objects' ;  rm -f '/home/exidez/bin/git-describe' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-describe' ;  rm -f '/home/exidez/bin/git-diff' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-diff' ;  rm -f '/home/exidez/bin/git-diff-files' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-diff-files' ;  rm -f '/home/exidez/bin/git-diff-index' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-diff-index' ;  rm -f '/home/exidez/bin/git-diff-tree' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-diff-tree' ;  rm -f '/home/exidez/bin/git-fetch--tool' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-fetch--tool' ;  rm -f '/home/exidez/bin/git-fmt-merge-msg' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-fmt-merge-msg' ;  rm -f '/home/exidez/bin/git-for-each-ref' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-for-each-ref' ;  rm -f '/home/exidez/bin/git-fsck' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-fsck' ;  rm -f '/home/exidez/bin/git-gc' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-gc' ;  rm -f '/home/exidez/bin/git-grep' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-grep' ;  rm -f '/home/exidez/bin/git-init-db' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-init-db' ;  rm -f '/home/exidez/bin/git-log' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-log' ;  rm -f '/home/exidez/bin/git-ls-files' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-ls-files' ;  rm -f '/home/exidez/bin/git-ls-tree' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-ls-tree' ;  rm -f '/home/exidez/bin/git-mailinfo' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-mailinfo' ;  rm -f '/home/exidez/bin/git-mailsplit' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-mailsplit' ;  rm -f '/home/exidez/bin/git-merge-base' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-merge-base' ;  rm -f '/home/exidez/bin/git-merge-file' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-merge-file' ;  rm -f '/home/exidez/bin/git-mv' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-mv' ;  rm -f '/home/exidez/bin/git-name-rev' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-name-rev' ;  rm -f '/home/exidez/bin/git-pack-objects' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-pack-objects' ;  rm -f '/home/exidez/bin/git-prune' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-prune' ;  rm -f '/home/exidez/bin/git-prune-packed' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-prune-packed' ;  rm -f '/home/exidez/bin/git-push' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-push' ;  rm -f '/home/exidez/bin/git-read-tree' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-read-tree' ;  rm -f '/home/exidez/bin/git-reflog' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-reflog' ;  rm -f '/home/exidez/bin/git-config' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-config' ;  rm -f '/home/exidez/bin/git-rerere' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-rerere' ;  rm -f '/home/exidez/bin/git-rev-list' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-rev-list' ;  rm -f '/home/exidez/bin/git-rev-parse' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-rev-parse' ;  rm -f '/home/exidez/bin/git-revert' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-revert' ;  rm -f '/home/exidez/bin/git-rm' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-rm' ;  rm -f '/home/exidez/bin/git-runstatus' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-runstatus' ;  rm -f '/home/exidez/bin/git-shortlog' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-shortlog' ;  rm -f '/home/exidez/bin/git-show-branch' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-show-branch' ;  rm -f '/home/exidez/bin/git-stripspace' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-stripspace' ;  rm -f '/home/exidez/bin/git-symbolic-ref' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-symbolic-ref' ;  rm -f '/home/exidez/bin/git-tar-tree' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-tar-tree' ;  rm -f '/home/exidez/bin/git-unpack-objects' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-unpack-objects' ;  rm -f '/home/exidez/bin/git-update-index' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-update-index' ;  rm -f '/home/exidez/bin/git-update-ref' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-update-ref' ;  rm -f '/home/exidez/bin/git-upload-archive' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-upload-archive' ;  rm -f '/home/exidez/bin/git-verify-pack' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-verify-pack' ;  rm -f '/home/exidez/bin/git-write-tree' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-write-tree' ;  rm -f '/home/exidez/bin/git-show-ref' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-show-ref' ;  rm -f '/home/exidez/bin/git-pack-refs' && ln '/home/exidez/bin/git' '/home/exidez/bin/git-pack-refs' ;

---

### Post by jackbravo on 2007-05-14
So you couldn't install git???

can't see the error on your post. Post the last lines of you compile errors.

Also, found on another thread a better way to meet dependencies of a package:

```
sudo apt-get build-dep git-core
```

That will install all the dependencies needed to compile git-core, you can do the same for gitk,git-svn and others, then compile git. Good luck.

---

### Post by Vinze on 2007-05-21
Hey, I checkinstalled it which generated this package: [http://www.esnips.com/nsdoc/50f0dd4b-c433-4bb8-bcfd-a1ef0f19b19c](http://www.esnips.com/nsdoc/50f0dd4b-c433-4bb8-bcfd-a1ef0f19b19c)

You should still do ```
sudo apt-get build-dep git-core
``` and it is still possible that it won't work. It's 32 bits or something, whatever. Just try it and see if it works.

---

### Post by Vinze on 2007-05-25
Sorry, I just found out you needed an account for that link, here is a new one:

[http://filegunner.net/file-viewer.php?id=184609git_1.5.2-1_i386.deb](http://filegunner.net/file-viewer.php?id=184609git_1.5.2-1_i386.deb)

And I just installed that in a Xubuntu LiveCD, so there's no need to install anything in advance. Have fun!

---

### Post by imog on 2007-05-27
The version hosted on file gunner does not have curl support builtin and I received the following error:

Initialized empty Git repository in /home/imog/git-1.5.2/ipwraw/.git/
http transport not supported, rebuild Git with curl support

It appears as though that installed a very old version of git, but not the essential git-core package this thread was presumably started in reference to.

Before attempting that, I followed jackbravo's advice above which allowed me to do a make on git.  When I attempted to do a make install however, I get the same result as exidez above and git-core does not install successfully.

Thank you for the input.

---

### Post by jackbravo on 2007-05-28
What options did you guys used on the make process. And could you post your last lines of errors on the make install? maybe you need to do a sudo make install or something.

---

### Post by imog on 2007-05-29
> **jackbravo said:**
> What options did you guys used on the make process. And could you post your last lines of errors on the make install? maybe you need to do a sudo make install or something.

The previous user pretty much entered everything, but here is an all inclusive quote of what I did:

imog@ubuntu-laptop:~/git-1.5.2$ sudo make
Password or swipe finger: 
    SUBDIR git-gui
    SUBDIR perl
    SUBDIR templates
imog@ubuntu-laptop:~/git-1.5.2$ sudo make install
    SUBDIR git-gui
    SUBDIR perl
    SUBDIR templates
install -d -m755 '/home/imog/bin'
install -d -m755 '/home/imog/bin'
install git-convert-objects git-fetch-pack git-fsck git-hash-object git-index-pack git-local-fetch git-fast-import git-merge-base git-daemon git-merge-index git-mktag git-mktree git-patch-id git-peek-remote git-receive-pack git-send-pack git-shell git-show-index git-ssh-fetch git-ssh-upload git-unpack-file git-update-server-info git-upload-pack git-verify-pack git-pack-redundant git-var git-merge-tree git-imap-send git-merge-recursive  git-ssh-pull git-ssh-push git-http-fetch git-http-push git-bisect git-checkout git-clean git-clone git-commit git-fetch git-ls-remote git-merge-one-file git-mergetool git-parse-remote git-pull git-rebase git-repack git-request-pull git-reset git-sh-setup git-tag git-verify-tag git-applymbox git-applypatch git-am git-merge git-merge-stupid git-merge-octopus git-merge-resolve git-merge-ours git-lost-found git-quiltimport git-add--interactive git-archimport git-cvsimport git-relink git-cvsserver git-remote git-svnimport git-cvsexportcommit git-send-email git-svn git-status git-instaweb git-merge-subtree '/home/imog/bin'
install git '/home/imog/bin'
make -C templates DESTDIR='' install
make[1]: Entering directory `/home/imog/git-1.5.2/templates'
install -d -m755 '/home/imog/share//git-core/templates/'
(cd blt && tar cf - .) | \
        (cd '/home/imog/share//git-core/templates/' && tar xf -)
make[1]: Leaving directory `/home/imog/git-1.5.2/templates'
make -C perl prefix='/home/imog' install
make[1]: Entering directory `/home/imog/git-1.5.2/perl'
make[2]: Entering directory `/home/imog/git-1.5.2/perl'
Writing /home/imog/lib/perl/5.8.8/auto/Git/.packlist
Appending installation info to /home/imog/lib/perl/5.8.8/perllocal.pod
make[2]: Leaving directory `/home/imog/git-1.5.2/perl'
make[1]: Leaving directory `/home/imog/git-1.5.2/perl'
install gitk-wish '/home/imog/bin'/gitk
make -C git-gui install
make[1]: Entering directory `/home/imog/git-1.5.2/git-gui'
install -d -m755 '/home/imog/bin'
install git-gui '/home/imog/bin'
rm -f '/home/imog/bin/git-citool' && ln '/home/imog/bin/git-gui' '/home/imog/bin/git-citool' ;
install -d -m755 '/home/imog/share//git-gui/lib'
install -m644 lib/tclIndex '/home/imog/share//git-gui/lib'
install -m644 lib/blame.tcl '/home/imog/share//git-gui/lib' ;  install -m644 lib/branch.tcl '/home/imog/share//git-gui/lib' ;  install -m644 lib/browser.tcl '/home/imog/share//git-gui/lib' ;  install -m644 lib/class.tcl '/home/imog/share//git-gui/lib' ;  install -m644 lib/commit.tcl '/home/imog/share//git-gui/lib' ;  install -m644 lib/console.tcl '/home/imog/share//git-gui/lib' ;  install -m644 lib/database.tcl '/home/imog/share//git-gui/lib' ;  install -m644 lib/diff.tcl '/home/imog/share//git-gui/lib' ;  install -m644 lib/error.tcl '/home/imog/share//git-gui/lib' ;  install -m644 lib/index.tcl '/home/imog/share//git-gui/lib' ;  install -m644 lib/merge.tcl '/home/imog/share//git-gui/lib' ;  install -m644 lib/option.tcl '/home/imog/share//git-gui/lib' ;  install -m644 lib/remote.tcl '/home/imog/share//git-gui/lib' ;  install -m644 lib/shortcut.tcl '/home/imog/share//git-gui/lib' ;  install -m644 lib/transport.tcl '/home/imog/share//git-gui/lib' ;
make[1]: Leaving directory `/home/imog/git-1.5.2/git-gui'
if test 'z/home/imog/bin' != 'z/home/imog/bin'; \
        then \
                ln -f '/home/imog/bin/git' \
                        '/home/imog/bin/git' || \
                cp '/home/imog/bin/git' \
                        '/home/imog/bin/git'; \
        fi
rm -f '/home/imog/bin/git-format-patch' && ln '/home/imog/bin/git' '/home/imog/bin/git-format-patch' ;  rm -f '/home/imog/bin/git-show' && ln '/home/imog/bin/git' '/home/imog/bin/git-show' ;  rm -f '/home/imog/bin/git-whatchanged' && ln '/home/imog/bin/git' '/home/imog/bin/git-whatchanged' ;  rm -f '/home/imog/bin/git-cherry' && ln '/home/imog/bin/git' '/home/imog/bin/git-cherry' ;  rm -f '/home/imog/bin/git-get-tar-commit-id' && ln '/home/imog/bin/git' '/home/imog/bin/git-get-tar-commit-id' ;  rm -f '/home/imog/bin/git-init' && ln '/home/imog/bin/git' '/home/imog/bin/git-init' ;  rm -f '/home/imog/bin/git-repo-config' && ln '/home/imog/bin/git' '/home/imog/bin/git-repo-config' ;  rm -f '/home/imog/bin/git-fsck-objects' && ln '/home/imog/bin/git' '/home/imog/bin/git-fsck-objects' ;  rm -f '/home/imog/bin/git-cherry-pick' && ln '/home/imog/bin/git' '/home/imog/bin/git-cherry-pick' ;  rm -f '/home/imog/bin/git-add' && ln '/home/imog/bin/git' '/home/imog/bin/git-add' ;  rm -f '/home/imog/bin/git-annotate' && ln '/home/imog/bin/git' '/home/imog/bin/git-annotate' ;  rm -f '/home/imog/bin/git-apply' && ln '/home/imog/bin/git' '/home/imog/bin/git-apply' ;  rm -f '/home/imog/bin/git-archive' && ln '/home/imog/bin/git' '/home/imog/bin/git-archive' ;  rm -f '/home/imog/bin/git-blame' && ln '/home/imog/bin/git' '/home/imog/bin/git-blame' ;  rm -f '/home/imog/bin/git-branch' && ln '/home/imog/bin/git' '/home/imog/bin/git-branch' ;  rm -f '/home/imog/bin/git-bundle' && ln '/home/imog/bin/git' '/home/imog/bin/git-bundle' ;  rm -f '/home/imog/bin/git-cat-file' && ln '/home/imog/bin/git' '/home/imog/bin/git-cat-file' ;  rm -f '/home/imog/bin/git-check-attr' && ln '/home/imog/bin/git' '/home/imog/bin/git-check-attr' ;  rm -f '/home/imog/bin/git-checkout-index' && ln '/home/imog/bin/git' '/home/imog/bin/git-checkout-index' ;  rm -f '/home/imog/bin/git-check-ref-format' && ln '/home/imog/bin/git' '/home/imog/bin/git-check-ref-format' ;  rm -f '/home/imog/bin/git-commit-tree' && ln '/home/imog/bin/git' '/home/imog/bin/git-commit-tree' ;  rm -f '/home/imog/bin/git-count-objects' && ln '/home/imog/bin/git' '/home/imog/bin/git-count-objects' ;  rm -f '/home/imog/bin/git-describe' && ln '/home/imog/bin/git' '/home/imog/bin/git-describe' ;  rm -f '/home/imog/bin/git-diff' && ln '/home/imog/bin/git' '/home/imog/bin/git-diff' ;  rm -f '/home/imog/bin/git-diff-files' && ln '/home/imog/bin/git' '/home/imog/bin/git-diff-files' ;  rm -f '/home/imog/bin/git-diff-index' && ln '/home/imog/bin/git' '/home/imog/bin/git-diff-index' ;  rm -f '/home/imog/bin/git-diff-tree' && ln '/home/imog/bin/git' '/home/imog/bin/git-diff-tree' ;  rm -f '/home/imog/bin/git-fetch--tool' && ln '/home/imog/bin/git' '/home/imog/bin/git-fetch--tool' ;  rm -f '/home/imog/bin/git-fmt-merge-msg' && ln '/home/imog/bin/git' '/home/imog/bin/git-fmt-merge-msg' ;  rm -f '/home/imog/bin/git-for-each-ref' && ln '/home/imog/bin/git' '/home/imog/bin/git-for-each-ref' ;  rm -f '/home/imog/bin/git-fsck' && ln '/home/imog/bin/git' '/home/imog/bin/git-fsck' ;  rm -f '/home/imog/bin/git-gc' && ln '/home/imog/bin/git' '/home/imog/bin/git-gc' ;  rm -f '/home/imog/bin/git-grep' && ln '/home/imog/bin/git' '/home/imog/bin/git-grep' ;  rm -f '/home/imog/bin/git-init-db' && ln '/home/imog/bin/git' '/home/imog/bin/git-init-db' ;  rm -f '/home/imog/bin/git-log' && ln '/home/imog/bin/git' '/home/imog/bin/git-log' ;  rm -f '/home/imog/bin/git-ls-files' && ln '/home/imog/bin/git' '/home/imog/bin/git-ls-files' ;  rm -f '/home/imog/bin/git-ls-tree' && ln '/home/imog/bin/git' '/home/imog/bin/git-ls-tree' ;  rm -f '/home/imog/bin/git-mailinfo' && ln '/home/imog/bin/git' '/home/imog/bin/git-mailinfo' ;  rm -f '/home/imog/bin/git-mailsplit' && ln '/home/imog/bin/git' '/home/imog/bin/git-mailsplit' ;  rm -f '/home/imog/bin/git-merge-base' && ln '/home/imog/bin/git' '/home/imog/bin/git-merge-base' ;  rm -f '/home/imog/bin/git-merge-file' && ln '/home/imog/bin/git' '/home/imog/bin/git-merge-file' ;  rm -f '/home/imog/bin/git-mv' && ln '/home/imog/bin/git' '/home/imog/bin/git-mv' ;  rm -f '/home/imog/bin/git-name-rev' && ln '/home/imog/bin/git' '/home/imog/bin/git-name-rev' ;  rm -f '/home/imog/bin/git-pack-objects' && ln '/home/imog/bin/git' '/home/imog/bin/git-pack-objects' ;  rm -f '/home/imog/bin/git-prune' && ln '/home/imog/bin/git' '/home/imog/bin/git-prune' ;  rm -f '/home/imog/bin/git-prune-packed' && ln '/home/imog/bin/git' '/home/imog/bin/git-prune-packed' ;  rm -f '/home/imog/bin/git-push' && ln '/home/imog/bin/git' '/home/imog/bin/git-push' ;  rm -f '/home/imog/bin/git-read-tree' && ln '/home/imog/bin/git' '/home/imog/bin/git-read-tree' ;  rm -f '/home/imog/bin/git-reflog' && ln '/home/imog/bin/git' '/home/imog/bin/git-reflog' ;  rm -f '/home/imog/bin/git-config' && ln '/home/imog/bin/git' '/home/imog/bin/git-config' ;  rm -f '/home/imog/bin/git-rerere' && ln '/home/imog/bin/git' '/home/imog/bin/git-rerere' ;  rm -f '/home/imog/bin/git-rev-list' && ln '/home/imog/bin/git' '/home/imog/bin/git-rev-list' ;  rm -f '/home/imog/bin/git-rev-parse' && ln '/home/imog/bin/git' '/home/imog/bin/git-rev-parse' ;  rm -f '/home/imog/bin/git-revert' && ln '/home/imog/bin/git' '/home/imog/bin/git-revert' ;  rm -f '/home/imog/bin/git-rm' && ln '/home/imog/bin/git' '/home/imog/bin/git-rm' ;  rm -f '/home/imog/bin/git-runstatus' && ln '/home/imog/bin/git' '/home/imog/bin/git-runstatus' ;  rm -f '/home/imog/bin/git-shortlog' && ln '/home/imog/bin/git' '/home/imog/bin/git-shortlog' ;  rm -f '/home/imog/bin/git-show-branch' && ln '/home/imog/bin/git' '/home/imog/bin/git-show-branch' ;  rm -f '/home/imog/bin/git-stripspace' && ln '/home/imog/bin/git' '/home/imog/bin/git-stripspace' ;  rm -f '/home/imog/bin/git-symbolic-ref' && ln '/home/imog/bin/git' '/home/imog/bin/git-symbolic-ref' ;  rm -f '/home/imog/bin/git-tar-tree' && ln '/home/imog/bin/git' '/home/imog/bin/git-tar-tree' ;  rm -f '/home/imog/bin/git-unpack-objects' && ln '/home/imog/bin/git' '/home/imog/bin/git-unpack-objects' ;  rm -f '/home/imog/bin/git-update-index' && ln '/home/imog/bin/git' '/home/imog/bin/git-update-index' ;  rm -f '/home/imog/bin/git-update-ref' && ln '/home/imog/bin/git' '/home/imog/bin/git-update-ref' ;  rm -f '/home/imog/bin/git-upload-archive' && ln '/home/imog/bin/git' '/home/imog/bin/git-upload-archive' ;  rm -f '/home/imog/bin/git-verify-pack' && ln '/home/imog/bin/git' '/home/imog/bin/git-verify-pack' ;  rm -f '/home/imog/bin/git-write-tree' && ln '/home/imog/bin/git' '/home/imog/bin/git-write-tree' ;  rm -f '/home/imog/bin/git-show-ref' && ln '/home/imog/bin/git' '/home/imog/bin/git-show-ref' ;  rm -f '/home/imog/bin/git-pack-refs' && ln '/home/imog/bin/git' '/home/imog/bin/git-pack-refs' ;
imog@ubuntu-laptop:~/git-1.5.2$ 

Pay no attention to the swipe finger portion, I have biometrics enabled on my T60 and the results are the same whether the biometrics are on or off.  Note that the above did not leave me with a succesful install.  I'll keep looking into it, the biometrics were a pain, but I'm hoping this won't be as bad,

---

### Post by imog on 2007-05-29
double post

---

### Post by incubus on 2007-06-04
Hi.

I just tried it myself and it seems to work.  I'm on x86_64.

```

$ tar xzvf git-1.5.2.1.tar.gz
$ cd git-1.5.2.1/
$ sudo apt-get install checkinstall
$ sudo apt-get build-dep git-core
$ sudo checkinstall -D
  # or make && make install, if you don't like checkinstall

```

Looks like git is updated for Gutsy.  The problem is the dependency on a newer version of libc6.

incubus

---

### Post by heldr on 2007-06-04
I tried the instructions in the last post but when I try:

> $ sudo apt-get build-dep git-core

it complains I don't have some repository (without saying which one). Does anyone know which one it is?

Thanks.

Helder

---

### Post by jackbravo on 2007-06-04
Looks like it did installed git, just on your /home/name/bin dir instead of on /usr/local.

Maybe all you need to do is add your home bin directory to the PATH.
If you want to install git on /usr/local you need to specify it on the configure command via: --prefix=/usr/local
and then do a > make && sudo make install.

as for what repositories does git need.... Well, I'm not sure, I have universe, multiverse, and everything =P.
Good luck.

---

### Post by Roderik on 2007-06-11
FYI I did the following

```

apt-get build-dep git-core
apt-get install libssl-dev
vim Makefile // to change the prefix to /usr/local
make
make install

```

And it worked.

---

### Post by heldr on 2007-06-11
Ok, so here's what sort of brute-forcedly worked for me:

Added a "deb-src" for each "deb" in /etc/apt/sources.list and then did:

```
apt-get build-dep git-core
apt-get install libssl-dev
make configure
./configure --prefix=/usr/local
make
sudo make install
```

It didn't work without doing the ./configure first.

---

### Post by onlycyan on 2007-07-08
I installed git,  and tried all methods u guys mentioned. but when i try the following line, this happened:
cyan@cyan-working-machine:~$ git clone git://anongit.freedesktop.org/git/xorg/proto/glproto

git, the filemanager with GNU Interactive Tools, is now called gitfm.

If you are looking for git, Linus Torvald's content tracker, install
the cogito and git-core packages and see README.Debian and git(7).

This transition script will be removed in the debian stable
release after etch.

If you wish to complete the transition early, install git-core
and use (as root):
 update-alternatives --config git

Press RETURN to run gitfm


GNU Interactive Tools 4.3.20 (i686-pc-linux-gnu), 16:31:59 Nov  9 2006
GIT is free software; you can redistribute it and/or modify it under the
terms of the GNU General Public License as published by the Free Software
Foundation; either version 2, or (at your option) any later version.
Copyright (C) 1993-1999 Free Software Foundation, Inc.
Written by Tudor Hulubei and Andrei Pitis, Bucharest, Romania

/usr/bin/gitfm: fatal error: `chdir' failed: permission denied.
cyan@cyan-working-machine:~$
cyan@cyan-working-machine:~$ sudo update-alternatives --config git
There are 2 alternatives which provide `git'.

  Selection    Alternative
-----------------------------------------------
*+        1    /usr/bin/git.transition
          2    /usr/bin/git-scm

Press enter to keep the default[*], or type selection number:
cyan@cyan-working-machine:~$


and nothing happened.......umm...don't know what to do now....
any help?

---

### Post by jackbravo on 2007-07-08
so when you typed:

> sudo update-alternatives --config git

did you pressed "2" to select git-scm. That's what you need to do. scm means source control manager I believe =P. And right now ubuntu executes GNU Interactive Tools (git) when you run git, instead of git the source control manager.

---

### Post by chrono325 on 2007-07-11
In case anyone is interested, the easiest way for me to accomplish the task was to install [Prevu]("https://wiki.ubuntu.com/Prevu") and backport the Gutsy version of git.

For those interested, I have set up a repository [here]("https://labradoodle.haxney.org/ubuntu/").

---

### Post by Vinze on 2007-07-11
> **chrono325 said:**
> In case anyone is interested, the easiest way for me to accomplish the task was to install [Prevu]("https://wiki.ubuntu.com/Prevu") and backport the Gutsy version of git.

For those interested, I have set up a repository [here]("https://labradoodle.haxney.org/ubuntu/").

Wow, Prevu is awesome. Thanks!

---

### Post by celafon on 2007-07-15
The thing I dont get is: Why is Git 1.5 not in feisty fawn repos?

There are bug-fixes, it WORKS. That's the only thing that is a pain with ubuntu: non-mainstream software is rather old...

gotta compile it...   ](*,)

---

### Post by chrono325 on 2007-07-23
It is annoying to have to wait so long for new versions of things, especially when there is as much new functionality as when upgrading from git 1.4 to 1.5.

Interestingly (annoyingly) enough, the Gutsy version does not seem to have submodule support, which was something I was really looking forward to.

celafon, try my repository. It has worked flawlessly for me and is much easier than compiling yourself.

EDIT: It looks like submodule support is coming in version 1.5.3 which is not yet released (latest is 1.5.2.4). I hope 1.5.3 makes it to Gutsy.

---

### Post by chrono325 on 2007-07-25
Well it looks like there is no need for the prevu version since Feisty-backports got 1.5.2.3 on July 20.

---

