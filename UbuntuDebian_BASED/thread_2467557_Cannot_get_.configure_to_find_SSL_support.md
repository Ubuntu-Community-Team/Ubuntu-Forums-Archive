---
title: "Cannot get ./configure to find SSL support"
date: 2021-09-30
forum: Ubuntu/Debian BASED
---

### Post by fierce on 2021-09-30
Hi all, latest Debian user here.  I am trying to compile an IRC client that Debian doesn't seem to have a package for, and I am getting these errors during ./configure which I need to resolve, as I need to be able to connect to SSL servers

```

checking whether to enable SSL support... if available
checking for SSLeay in -lcrypto... no
configure: WARNING: OpenSSL not found, will not have SSL support.

```

I already have installed libssl-dev and openssl packages via apt-get, so I am unsure how to proceed.  Any assistance would be much appreciated!

Also, I typed 'find / |grep libcrypto' and there is definitely libcrypto.so and libcrypto.so.1.1 and related files in /usr/lib/i386-linux-gnu/ so I double don't get it

Thanks very much for your help

---

### Post by fierce on 2021-09-30
Also this is a section of the ./configure file which seems to pertain to this situation

```

echo "$as_me:$LINENO: checking whether to enable SSL support" >&5
echo $ECHO_N "checking whether to enable SSL support... $ECHO_C" >&6

# Check whether --with-ssl or --without-ssl was given.
if test "${with_ssl+set}" = set; then
  withval="$with_ssl"

else
  with_ssl=check
fi;

case "$with_ssl" in
    yes)
      echo "$as_me:$LINENO: result: yes" >&5
echo "${ECHO_T}yes" >&6
      ;;
    check)
      echo "$as_me:$LINENO: result: if available" >&5
echo "${ECHO_T}if available" >&6
      ;;
    no)
      echo "$as_me:$LINENO: result: no" >&5
echo "${ECHO_T}no" >&6
      ;;
    *)
      echo "$as_me:$LINENO: result: yes" >&5
echo "${ECHO_T}yes" >&6
      CFLAGS="$CFLAGS -I${with_ssl}/include"
      LDFLAGS="$LDFLAGS -L${with_ssl}/lib"
      with_ssl=yes
      ;;
esac
case "$with_ssl" in
    yes|check)

echo "$as_me:$LINENO: checking for SSLeay in -lcrypto" >&5
echo $ECHO_N "checking for SSLeay in -lcrypto... $ECHO_C" >&6
if test "${ac_cv_lib_crypto_SSLeay+set}" = set; then
  echo $ECHO_N "(cached) $ECHO_C" >&6
else
  ac_check_lib_save_LIBS=$LIBS
LIBS="-lcrypto  $LIBS"
cat >conftest.$ac_ext <<_ACEOF
/* confdefs.h.  */
_ACEOF
cat confdefs.h >>conftest.$ac_ext
cat >>conftest.$ac_ext <<_ACEOF
/* end confdefs.h.  */

```

not sure if this helps!

---

### Post by fierce on 2021-09-30
I found this previously asked post on Google: [https://stackoverflow.com/questions/49929780/could-not-find-openssl-when-compiling-bitchx](https://stackoverflow.com/questions/49929780/could-not-find-openssl-when-compiling-bitchx)

Which claims it needs an older libssl version, libssl1.0-dev to be exact.

However when I try to apt-get install libssl1.0-dev it says there is no installation candidate, and fails.

Is there any way to temporarily get libssl1.0 back?  It's because this IRC client is discontinued and very old, but I'd still like to use it if possible

---

