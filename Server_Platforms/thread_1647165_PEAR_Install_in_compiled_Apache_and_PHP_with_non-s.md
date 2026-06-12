---
title: "PEAR Install in compiled Apache and PHP with non-standard install prefix"
date: 2010-12-16
forum: Server Platforms
---

### Post by STOIE on 2010-12-16
Hi all,

I have a bit of an issue, I have compiled apache and php (2.2.17 and 5.2.15) and have an issue getting a site up and running that requires PEAR::HTML_Template_IT.

Problem is I believe that php has no idea of PEAR and it's configuration.

Anyway, when I open a PEAR_Info_toHtml() page, I get the following error and nothing in the apache logs: "No valid PEAR directory".

php.ini "include_path = ".:/data00/sw/php/current/lib/php:/data00/sw/php/current/lib/php/PEAR"

My directory structure:
(note /data00/sw/php/current = /data00/sw/php/5.2.15)

/data00/sw/php/current/
/data00/sw/php/current/man
/data00/sw/php/current/man/man1
/data00/sw/php/current/man/man1/php-config.1
/data00/sw/php/current/man/man1/phpize.1
/data00/sw/php/current/man/man1/php.1
/data00/sw/php/current/include
/data00/sw/php/current/include/php
/data00/sw/php/current/include/php/TSRM
/data00/sw/php/current/include/php/TSRM/TSRM.h
/data00/sw/php/current/include/php/TSRM/readdir.h
/data00/sw/php/current/include/php/TSRM/acconfig.h
/data00/sw/php/current/include/php/TSRM/tsrm_nw.h
/data00/sw/php/current/include/php/TSRM/tsrm_win32.h
/data00/sw/php/current/include/php/TSRM/tsrm_virtual_cwd.h
/data00/sw/php/current/include/php/TSRM/tsrm_strtok_r.h
/data00/sw/php/current/include/php/TSRM/tsrm_config.w32.h
/data00/sw/php/current/include/php/TSRM/tsrm_config_common.h
/data00/sw/php/current/include/php/TSRM/tsrm_config.h
/data00/sw/php/current/include/php/include
/data00/sw/php/current/include/php/regex
/data00/sw/php/current/include/php/regex/regex.h
/data00/sw/php/current/include/php/regex/utils.h
/data00/sw/php/current/include/php/regex/regex_extra.h
/data00/sw/php/current/include/php/regex/regex2.h
/data00/sw/php/current/include/php/regex/cname.h
/data00/sw/php/current/include/php/regex/cclass.h
/data00/sw/php/current/include/php/ext
/data00/sw/php/current/include/php/ext/filter
/data00/sw/php/current/include/php/ext/filter/php_filter.h
/data00/sw/php/current/include/php/ext/hash
/data00/sw/php/current/include/php/ext/hash/php_hash_haval.h
/data00/sw/php/current/include/php/ext/hash/php_hash_adler32.h
/data00/sw/php/current/include/php/ext/hash/php_hash_types.h
/data00/sw/php/current/include/php/ext/hash/php_hash.h
/data00/sw/php/current/include/php/ext/hash/php_hash_md.h
/data00/sw/php/current/include/php/ext/hash/php_hash_tiger.h
/data00/sw/php/current/include/php/ext/hash/php_hash_sha.h
/data00/sw/php/current/include/php/ext/hash/php_hash_snefru.h
/data00/sw/php/current/include/php/ext/hash/php_hash_whirlpool.h
/data00/sw/php/current/include/php/ext/hash/php_hash_ripemd.h
/data00/sw/php/current/include/php/ext/hash/php_hash_crc32.h
/data00/sw/php/current/include/php/ext/hash/php_hash_gost.h
/data00/sw/php/current/include/php/ext/session
/data00/sw/php/current/include/php/ext/session/php_session.h
/data00/sw/php/current/include/php/ext/session/mod_user.h
/data00/sw/php/current/include/php/ext/session/mod_files.h
/data00/sw/php/current/include/php/ext/date
/data00/sw/php/current/include/php/ext/date/lib
/data00/sw/php/current/include/php/ext/date/lib/timelib_structs.h
/data00/sw/php/current/include/php/ext/date/lib/timelib.h
/data00/sw/php/current/include/php/ext/date/lib/timelib_config.h
/data00/sw/php/current/include/php/ext/date/php_date.h
/data00/sw/php/current/include/php/ext/standard
/data00/sw/php/current/include/php/ext/standard/microtime.h
/data00/sw/php/current/include/php/ext/standard/crc32.h
/data00/sw/php/current/include/php/ext/standard/php_iptc.h
/data00/sw/php/current/include/php/ext/standard/scanf.h
/data00/sw/php/current/include/php/ext/standard/css.h
/data00/sw/php/current/include/php/ext/standard/exec.h
/data00/sw/php/current/include/php/ext/standard/php_lcg.h
/data00/sw/php/current/include/php/ext/standard/php_uuencode.h
/data00/sw/php/current/include/php/ext/standard/php_math.h
/data00/sw/php/current/include/php/ext/standard/file.h
/data00/sw/php/current/include/php/ext/standard/md5.h
/data00/sw/php/current/include/php/ext/standard/pageinfo.h
/data00/sw/php/current/include/php/ext/standard/credits_ext.h
/data00/sw/php/current/include/php/ext/standard/basic_functions.h
/data00/sw/php/current/include/php/ext/standard/cyr_convert.h
/data00/sw/php/current/include/php/ext/standard/php_rand.h
/data00/sw/php/current/include/php/ext/standard/php_array.h
/data00/sw/php/current/include/php/ext/standard/php_ext_syslog.h
/data00/sw/php/current/include/php/ext/standard/uniqid.h
/data00/sw/php/current/include/php/ext/standard/php_standard.h
/data00/sw/php/current/include/php/ext/standard/credits.h
/data00/sw/php/current/include/php/ext/standard/quot_print.h
/data00/sw/php/current/include/php/ext/standard/php_browscap.h
/data00/sw/php/current/include/php/ext/standard/streamsfuncs.h
/data00/sw/php/current/include/php/ext/standard/url_scanner_ex.h
/data00/sw/php/current/include/php/ext/standard/php_var.h
/data00/sw/php/current/include/php/ext/standard/php_dir.h
/data00/sw/php/current/include/php/ext/standard/info.h
/data00/sw/php/current/include/php/ext/standard/php_assert.h
/data00/sw/php/current/include/php/ext/standard/php_dns.h
/data00/sw/php/current/include/php/ext/standard/php_mail.h
/data00/sw/php/current/include/php/ext/standard/php_link.h
/data00/sw/php/current/include/php/ext/standard/php_ftok.h
/data00/sw/php/current/include/php/ext/standard/proc_open.h
/data00/sw/php/current/include/php/ext/standard/php_type.h
/data00/sw/php/current/include/php/ext/standard/php_fopen_wrappers.h
/data00/sw/php/current/include/php/ext/standard/php_smart_str.h
/data00/sw/php/current/include/php/ext/standard/dl.h
/data00/sw/php/current/include/php/ext/standard/url.h
/data00/sw/php/current/include/php/ext/standard/sha1.h
/data00/sw/php/current/include/php/ext/standard/php_crypt.h
/data00/sw/php/current/include/php/ext/standard/php_string.h
/data00/sw/php/current/include/php/ext/standard/php_filestat.h
/data00/sw/php/current/include/php/ext/standard/php_image.h
/data00/sw/php/current/include/php/ext/standard/fsock.h
/data00/sw/php/current/include/php/ext/standard/php_versioning.h
/data00/sw/php/current/include/php/ext/standard/datetime.h
/data00/sw/php/current/include/php/ext/standard/credits_sapi.h
/data00/sw/php/current/include/php/ext/standard/php_incomplete_class.h
/data00/sw/php/current/include/php/ext/standard/html.h
/data00/sw/php/current/include/php/ext/standard/reg.h
/data00/sw/php/current/include/php/ext/standard/php_smart_str_public.h
/data00/sw/php/current/include/php/ext/standard/flock_compat.h
/data00/sw/php/current/include/php/ext/standard/php_http.h
/data00/sw/php/current/include/php/ext/standard/head.h
/data00/sw/php/current/include/php/ext/standard/php_metaphone.h
/data00/sw/php/current/include/php/ext/standard/pack.h
/data00/sw/php/current/include/php/ext/standard/base64.h
/data00/sw/php/current/include/php/ext/iconv
/data00/sw/php/current/include/php/ext/iconv/php_have_bsd_iconv.h
/data00/sw/php/current/include/php/ext/iconv/php_php_iconv_impl.h
/data00/sw/php/current/include/php/ext/iconv/php_iconv_supports_errno.h
/data00/sw/php/current/include/php/ext/iconv/php_have_iconv.h
/data00/sw/php/current/include/php/ext/iconv/php_have_ibm_iconv.h
/data00/sw/php/current/include/php/ext/iconv/php_have_libiconv.h
/data00/sw/php/current/include/php/ext/iconv/php_iconv.h
/data00/sw/php/current/include/php/ext/iconv/php_have_glibc_iconv.h
/data00/sw/php/current/include/php/ext/iconv/php_iconv_aliased_libiconv.h
/data00/sw/php/current/include/php/ext/iconv/php_php_iconv_h_path.h
/data00/sw/php/current/include/php/ext/sqlite
/data00/sw/php/current/include/php/ext/sqlite/libsqlite
/data00/sw/php/current/include/php/ext/sqlite/libsqlite/src
/data00/sw/php/current/include/php/ext/sqlite/libsqlite/src/sqlite.h
/data00/sw/php/current/include/php/ext/libxml
/data00/sw/php/current/include/php/ext/libxml/php_libxml.h
/data00/sw/php/current/include/php/ext/xml
/data00/sw/php/current/include/php/ext/xml/expat_compat.h
/data00/sw/php/current/include/php/ext/xml/php_xml.h
/data00/sw/php/current/include/php/ext/pdo
/data00/sw/php/current/include/php/ext/pdo/php_pdo.h
/data00/sw/php/current/include/php/ext/pdo/php_pdo_driver.h
/data00/sw/php/current/include/php/ext/pcre
/data00/sw/php/current/include/php/ext/pcre/php_pcre.h
/data00/sw/php/current/include/php/ext/pcre/pcrelib
/data00/sw/php/current/include/php/ext/pcre/pcrelib/pcreposix.h
/data00/sw/php/current/include/php/ext/pcre/pcrelib/pcre.h
/data00/sw/php/current/include/php/ext/pcre/pcrelib/pcre_internal.h
/data00/sw/php/current/include/php/ext/pcre/pcrelib/ucp.h
/data00/sw/php/current/include/php/ext/pcre/pcrelib/config.h
/data00/sw/php/current/include/php/ext/spl
/data00/sw/php/current/include/php/ext/spl/spl_array.h
/data00/sw/php/current/include/php/ext/spl/spl_sxe.h
/data00/sw/php/current/include/php/ext/spl/spl_iterators.h
/data00/sw/php/current/include/php/ext/spl/spl_engine.h
/data00/sw/php/current/include/php/ext/spl/php_spl.h
/data00/sw/php/current/include/php/ext/spl/spl_functions.h
/data00/sw/php/current/include/php/ext/spl/spl_directory.h
/data00/sw/php/current/include/php/ext/spl/spl_exceptions.h
/data00/sw/php/current/include/php/ext/spl/spl_observer.h
/data00/sw/php/current/include/php/ext/dom
/data00/sw/php/current/include/php/ext/dom/xml_common.h
/data00/sw/php/current/include/php/ext/json
/data00/sw/php/current/include/php/ext/json/php_json.h
/data00/sw/php/current/include/php/Zend
/data00/sw/php/current/include/php/Zend/zend_dynamic_array.h
/data00/sw/php/current/include/php/Zend/zend_vm_opcodes.h
/data00/sw/php/current/include/php/Zend/zend_stack.h
/data00/sw/php/current/include/php/Zend/FlexLexer.h
/data00/sw/php/current/include/php/Zend/zend_strtod.h
/data00/sw/php/current/include/php/Zend/zend_exceptions.h
/data00/sw/php/current/include/php/Zend/zend_API.h
/data00/sw/php/current/include/php/Zend/zend_ini_scanner.h
/data00/sw/php/current/include/php/Zend/zend_list.h
/data00/sw/php/current/include/php/Zend/zend_extensions.h
/data00/sw/php/current/include/php/Zend/zend_operators.h
/data00/sw/php/current/include/php/Zend/zend_modules.h
/data00/sw/php/current/include/php/Zend/zend_objects.h
/data00/sw/php/current/include/php/Zend/zend_interfaces.h
/data00/sw/php/current/include/php/Zend/zend_constants.h
/data00/sw/php/current/include/php/Zend/zend_execute.h
/data00/sw/php/current/include/php/Zend/zend_errors.h
/data00/sw/php/current/include/php/Zend/zend_config.h
/data00/sw/php/current/include/php/Zend/zend_config.w32.h
/data00/sw/php/current/include/php/Zend/zend_ini.h
/data00/sw/php/current/include/php/Zend/zend_iterators.h
/data00/sw/php/current/include/php/Zend/acconfig.h
/data00/sw/php/current/include/php/Zend/zend_globals.h
/data00/sw/php/current/include/php/Zend/zend_llist.h
/data00/sw/php/current/include/php/Zend/zend_istdiostream.h
/data00/sw/php/current/include/php/Zend/zend_compile.h
/data00/sw/php/current/include/php/Zend/zend_ptr_stack.h
/data00/sw/php/current/include/php/Zend/zend_qsort.h
/data00/sw/php/current/include/php/Zend/zend_multiply.h
/data00/sw/php/current/include/php/Zend/zend_variables.h
/data00/sw/php/current/include/php/Zend/zend_alloc.h
/data00/sw/php/current/include/php/Zend/zend_language_parser.h
/data00/sw/php/current/include/php/Zend/zend_object_handlers.h
/data00/sw/php/current/include/php/Zend/zend_indent.h
/data00/sw/php/current/include/php/Zend/zend_ts_hash.h
/data00/sw/php/current/include/php/Zend/zend_fast_cache.h
/data00/sw/php/current/include/php/Zend/zend_hash.h
/data00/sw/php/current/include/php/Zend/zend_vm_def.h
/data00/sw/php/current/include/php/Zend/zend_language_scanner.h
/data00/sw/php/current/include/php/Zend/zend_stream.h
/data00/sw/php/current/include/php/Zend/zend_config.nw.h
/data00/sw/php/current/include/php/Zend/zend_multibyte.h
/data00/sw/php/current/include/php/Zend/zend_vm_execute.h
/data00/sw/php/current/include/php/Zend/zend_builtin_functions.h
/data00/sw/php/current/include/php/Zend/zend_ini_parser.h
/data00/sw/php/current/include/php/Zend/zend_objects_API.h
/data00/sw/php/current/include/php/Zend/zend_highlight.h
/data00/sw/php/current/include/php/Zend/zend_static_allocator.h
/data00/sw/php/current/include/php/Zend/zend_types.h
/data00/sw/php/current/include/php/Zend/zend_vm.h
/data00/sw/php/current/include/php/Zend/zend.h
/data00/sw/php/current/include/php/Zend/zend_globals_macros.h
/data00/sw/php/current/include/php/main
/data00/sw/php/current/include/php/main/php_version.h
/data00/sw/php/current/include/php/main/php_reentrancy.h
/data00/sw/php/current/include/php/main/snprintf.h
/data00/sw/php/current/include/php/main/php_scandir.h
/data00/sw/php/current/include/php/main/php_syslog.h
/data00/sw/php/current/include/php/main/php3_compat.h
/data00/sw/php/current/include/php/main/build-defs.h
/data00/sw/php/current/include/php/main/php_streams.h
/data00/sw/php/current/include/php/main/php_main.h
/data00/sw/php/current/include/php/main/php_open_temporary_file.h
/data00/sw/php/current/include/php/main/php_network.h
/data00/sw/php/current/include/php/main/php_regex.h
/data00/sw/php/current/include/php/main/php_logos.h
/data00/sw/php/current/include/php/main/php_content_types.h
/data00/sw/php/current/include/php/main/php_output.h
/data00/sw/php/current/include/php/main/php_variables.h
/data00/sw/php/current/include/php/main/rfc1867.h
/data00/sw/php/current/include/php/main/logos.h
/data00/sw/php/current/include/php/main/php_config.h
/data00/sw/php/current/include/php/main/php_globals.h
/data00/sw/php/current/include/php/main/php_ini.h
/data00/sw/php/current/include/php/main/config.w32.h
/data00/sw/php/current/include/php/main/streams
/data00/sw/php/current/include/php/main/streams/php_streams_int.h
/data00/sw/php/current/include/php/main/streams/php_stream_plain_wrapper.h
/data00/sw/php/current/include/php/main/streams/php_stream_filter_api.h
/data00/sw/php/current/include/php/main/streams/php_stream_transport.h
/data00/sw/php/current/include/php/main/streams/php_stream_mmap.h
/data00/sw/php/current/include/php/main/streams/php_stream_userspace.h
/data00/sw/php/current/include/php/main/streams/php_stream_context.h
/data00/sw/php/current/include/php/main/SAPI.h
/data00/sw/php/current/include/php/main/php_compat.h
/data00/sw/php/current/include/php/main/php.h
/data00/sw/php/current/include/php/main/fopen_wrappers.h
/data00/sw/php/current/include/php/main/php_memory_streams.h
/data00/sw/php/current/include/php/main/win95nt.h
/data00/sw/php/current/include/php/main/php_ticks.h
/data00/sw/php/current/include/php/main/spprintf.h
/data00/sw/php/current/include/php/main/safe_mode.h
/data00/sw/php/current/bin
/data00/sw/php/current/bin/php
/data00/sw/php/current/bin/pear
/data00/sw/php/current/bin/php-config
/data00/sw/php/current/bin/pearinfo
/data00/sw/php/current/bin/peardev
/data00/sw/php/current/bin/pecl
/data00/sw/php/current/bin/phpize
/data00/sw/php/current/etc
/data00/sw/php/current/etc/pear.conf
/data00/sw/php/current/lib
/data00/sw/php/current/lib/php
/data00/sw/php/current/lib/php/.filemap
/data00/sw/php/current/lib/php/Console
/data00/sw/php/current/lib/php/Console/Getargs.php
/data00/sw/php/current/lib/php/Console/Getopt.php
/data00/sw/php/current/lib/php/PEAR
/data00/sw/php/current/lib/php/PEAR/Frontend
/data00/sw/php/current/lib/php/PEAR/Frontend/CLI.php
/data00/sw/php/current/lib/php/PEAR/Info
/data00/sw/php/current/lib/php/PEAR/Info/Cli.php
/data00/sw/php/current/lib/php/PEAR/Dependency2.php
/data00/sw/php/current/lib/php/PEAR/Common.php
/data00/sw/php/current/lib/php/PEAR/Installer
/data00/sw/php/current/lib/php/PEAR/Installer/Role.php
/data00/sw/php/current/lib/php/PEAR/Installer/Role
/data00/sw/php/current/lib/php/PEAR/Installer/Role/Script.php
/data00/sw/php/current/lib/php/PEAR/Installer/Role/Cfg.php
/data00/sw/php/current/lib/php/PEAR/Installer/Role/Www.xml
/data00/sw/php/current/lib/php/PEAR/Installer/Role/Ext.php
/data00/sw/php/current/lib/php/PEAR/Installer/Role/Common.php
/data00/sw/php/current/lib/php/PEAR/Installer/Role/Data.xml
/data00/sw/php/current/lib/php/PEAR/Installer/Role/Test.xml
/data00/sw/php/current/lib/php/PEAR/Installer/Role/Data.php
/data00/sw/php/current/lib/php/PEAR/Installer/Role/Doc.php
/data00/sw/php/current/lib/php/PEAR/Installer/Role/Script.xml
/data00/sw/php/current/lib/php/PEAR/Installer/Role/Cfg.xml
/data00/sw/php/current/lib/php/PEAR/Installer/Role/Doc.xml
/data00/sw/php/current/lib/php/PEAR/Installer/Role/Test.php
/data00/sw/php/current/lib/php/PEAR/Installer/Role/Php.xml
/data00/sw/php/current/lib/php/PEAR/Installer/Role/Ext.xml
/data00/sw/php/current/lib/php/PEAR/Installer/Role/Src.xml
/data00/sw/php/current/lib/php/PEAR/Installer/Role/Www.php
/data00/sw/php/current/lib/php/PEAR/Installer/Role/Php.php
/data00/sw/php/current/lib/php/PEAR/Installer/Role/Src.php
/data00/sw/php/current/lib/php/PEAR/Command
/data00/sw/php/current/lib/php/PEAR/Command/Mirror.xml
/data00/sw/php/current/lib/php/PEAR/Command/Common.php
/data00/sw/php/current/lib/php/PEAR/Command/Mirror.php
/data00/sw/php/current/lib/php/PEAR/Command/Auth.xml
/data00/sw/php/current/lib/php/PEAR/Command/Registry.xml
/data00/sw/php/current/lib/php/PEAR/Command/Auth.php
/data00/sw/php/current/lib/php/PEAR/Command/Config.xml
/data00/sw/php/current/lib/php/PEAR/Command/Test.xml
/data00/sw/php/current/lib/php/PEAR/Command/Remote.xml
/data00/sw/php/current/lib/php/PEAR/Command/Channels.xml
/data00/sw/php/current/lib/php/PEAR/Command/Config.php
/data00/sw/php/current/lib/php/PEAR/Command/Package.php
/data00/sw/php/current/lib/php/PEAR/Command/Install.php
/data00/sw/php/current/lib/php/PEAR/Command/Build.php
/data00/sw/php/current/lib/php/PEAR/Command/Install.xml
/data00/sw/php/current/lib/php/PEAR/Command/Remote.php
/data00/sw/php/current/lib/php/PEAR/Command/Build.xml
/data00/sw/php/current/lib/php/PEAR/Command/Test.php
/data00/sw/php/current/lib/php/PEAR/Command/Package.xml
/data00/sw/php/current/lib/php/PEAR/Command/Channels.php
/data00/sw/php/current/lib/php/PEAR/Command/Pickle.xml
/data00/sw/php/current/lib/php/PEAR/Command/Registry.php
/data00/sw/php/current/lib/php/PEAR/Command/Pickle.php
/data00/sw/php/current/lib/php/PEAR/Frontend.php
/data00/sw/php/current/lib/php/PEAR/Autoloader.php
/data00/sw/php/current/lib/php/PEAR/Validate.php
/data00/sw/php/current/lib/php/PEAR/Task
/data00/sw/php/current/lib/php/PEAR/Task/Unixeol.php
/data00/sw/php/current/lib/php/PEAR/Task/Postinstallscript.php
/data00/sw/php/current/lib/php/PEAR/Task/Common.php
/data00/sw/php/current/lib/php/PEAR/Task/Unixeol
/data00/sw/php/current/lib/php/PEAR/Task/Unixeol/rw.php
/data00/sw/php/current/lib/php/PEAR/Task/Replace.php
/data00/sw/php/current/lib/php/PEAR/Task/Postinstallscript
/data00/sw/php/current/lib/php/PEAR/Task/Postinstallscript/rw.php
/data00/sw/php/current/lib/php/PEAR/Task/Windowseol
/data00/sw/php/current/lib/php/PEAR/Task/Windowseol/rw.php
/data00/sw/php/current/lib/php/PEAR/Task/Replace
/data00/sw/php/current/lib/php/PEAR/Task/Replace/rw.php
/data00/sw/php/current/lib/php/PEAR/Task/Windowseol.php
/data00/sw/php/current/lib/php/PEAR/ErrorStack.php
/data00/sw/php/current/lib/php/PEAR/ChannelFile
/data00/sw/php/current/lib/php/PEAR/ChannelFile/Parser.php
/data00/sw/php/current/lib/php/PEAR/Command.php
/data00/sw/php/current/lib/php/PEAR/RunTest.php
/data00/sw/php/current/lib/php/PEAR/Config.php
/data00/sw/php/current/lib/php/PEAR/REST.php
/data00/sw/php/current/lib/php/PEAR/REST
/data00/sw/php/current/lib/php/PEAR/REST/10.php
/data00/sw/php/current/lib/php/PEAR/REST/13.php
/data00/sw/php/current/lib/php/PEAR/REST/11.php
/data00/sw/php/current/lib/php/PEAR/Info.php
/data00/sw/php/current/lib/php/PEAR/Exception.php
/data00/sw/php/current/lib/php/PEAR/PackageFile
/data00/sw/php/current/lib/php/PEAR/PackageFile/v2.php
/data00/sw/php/current/lib/php/PEAR/PackageFile/v2
/data00/sw/php/current/lib/php/PEAR/PackageFile/v2/rw.php
/data00/sw/php/current/lib/php/PEAR/PackageFile/v2/Validator.php
/data00/sw/php/current/lib/php/PEAR/PackageFile/Parser
/data00/sw/php/current/lib/php/PEAR/PackageFile/Parser/v2.php
/data00/sw/php/current/lib/php/PEAR/PackageFile/Parser/v1.php
/data00/sw/php/current/lib/php/PEAR/PackageFile/Generator
/data00/sw/php/current/lib/php/PEAR/PackageFile/Generator/v2.php
/data00/sw/php/current/lib/php/PEAR/PackageFile/Generator/v1.php
/data00/sw/php/current/lib/php/PEAR/PackageFile/v1.php
/data00/sw/php/current/lib/php/PEAR/Validator
/data00/sw/php/current/lib/php/PEAR/Validator/PECL.php
/data00/sw/php/current/lib/php/PEAR/Downloader
/data00/sw/php/current/lib/php/PEAR/Downloader/Package.php
/data00/sw/php/current/lib/php/PEAR/DependencyDB.php
/data00/sw/php/current/lib/php/PEAR/Packager.php
/data00/sw/php/current/lib/php/PEAR/Builder.php
/data00/sw/php/current/lib/php/PEAR/PackageFile.php
/data00/sw/php/current/lib/php/PEAR/FixPHP5PEARWarnings.php
/data00/sw/php/current/lib/php/PEAR/Downloader.php
/data00/sw/php/current/lib/php/PEAR/Registry.php
/data00/sw/php/current/lib/php/PEAR/ChannelFile.php
/data00/sw/php/current/lib/php/PEAR/Installer.php
/data00/sw/php/current/lib/php/PEAR/XMLParser.php
/data00/sw/php/current/lib/php/.depdblock
/data00/sw/php/current/lib/php/data
/data00/sw/php/current/lib/php/data/PEAR
/data00/sw/php/current/lib/php/data/PEAR/package.dtd
/data00/sw/php/current/lib/php/data/PEAR/template.spec
/data00/sw/php/current/lib/php/data/Structures_Graph
/data00/sw/php/current/lib/php/data/Structures_Graph/LICENSE
/data00/sw/php/current/lib/php/data/PEAR_Info
/data00/sw/php/current/lib/php/data/PEAR_Info/pearinfo.css
/data00/sw/php/current/lib/php/peclcmd.php
/data00/sw/php/current/lib/php/OS
/data00/sw/php/current/lib/php/OS/Guess.php
/data00/sw/php/current/lib/php/HTML
/data00/sw/php/current/lib/php/HTML/Template
/data00/sw/php/current/lib/php/HTML/Template/ITX.php
/data00/sw/php/current/lib/php/HTML/Template/IT.php
/data00/sw/php/current/lib/php/HTML/Template/IT_Error.php
/data00/sw/php/current/lib/php/System.php
/data00/sw/php/current/lib/php/build
/data00/sw/php/current/lib/php/build/acinclude.m4
/data00/sw/php/current/lib/php/build/shtool
/data00/sw/php/current/lib/php/build/config.guess
/data00/sw/php/current/lib/php/build/Makefile.global
/data00/sw/php/current/lib/php/build/config.sub
/data00/sw/php/current/lib/php/build/scan_makefile_in.awk
/data00/sw/php/current/lib/php/build/ltmain.sh
/data00/sw/php/current/lib/php/build/mkdep.awk
/data00/sw/php/current/lib/php/build/phpize.m4
/data00/sw/php/current/lib/php/build/libtool.m4
/data00/sw/php/current/lib/php/build/run-tests.php
/data00/sw/php/current/lib/php/doc
/data00/sw/php/current/lib/php/doc/PEAR
/data00/sw/php/current/lib/php/doc/PEAR/LICENSE
/data00/sw/php/current/lib/php/doc/PEAR/README
/data00/sw/php/current/lib/php/doc/PEAR/INSTALL
/data00/sw/php/current/lib/php/doc/XML_Util
/data00/sw/php/current/lib/php/doc/XML_Util/examples
/data00/sw/php/current/lib/php/doc/XML_Util/examples/example2.php
/data00/sw/php/current/lib/php/doc/XML_Util/examples/example.php
/data00/sw/php/current/lib/php/doc/Console_Getargs
/data00/sw/php/current/lib/php/doc/Console_Getargs/examples
/data00/sw/php/current/lib/php/doc/Console_Getargs/examples/example2.php
/data00/sw/php/current/lib/php/doc/Console_Getargs/examples/example.php
/data00/sw/php/current/lib/php/doc/Structures_Graph
/data00/sw/php/current/lib/php/doc/Structures_Graph/docs
/data00/sw/php/current/lib/php/doc/Structures_Graph/docs/html
/data00/sw/php/current/lib/php/doc/Structures_Graph/docs/html/elementindex_Structures_Graph.html
/data00/sw/php/current/lib/php/doc/Structures_Graph/docs/html/media
/data00/sw/php/current/lib/php/doc/Structures_Graph/docs/html/media/banner.css
/data00/sw/php/current/lib/php/doc/Structures_Graph/docs/html/media/stylesheet.css
/data00/sw/php/current/lib/php/doc/Structures_Graph/docs/html/classtrees_Structures_Graph.html
/data00/sw/php/current/lib/php/doc/Structures_Graph/docs/html/elementindex.html
/data00/sw/php/current/lib/php/doc/Structures_Graph/docs/html/index.html
/data00/sw/php/current/lib/php/doc/Structures_Graph/docs/html/todolist.html
/data00/sw/php/current/lib/php/doc/Structures_Graph/docs/html/Structures_Graph
/data00/sw/php/current/lib/php/doc/Structures_Graph/docs/html/Structures_Graph/Structures_Graph_Manipulator_TopologicalSorter.html
/data00/sw/php/current/lib/php/doc/Structures_Graph/docs/html/Structures_Graph/_Structures_Graph_Node_php.html
/data00/sw/php/current/lib/php/doc/Structures_Graph/docs/html/Structures_Graph/Structures_Graph_Manipulator_AcyclicTest.html
/data00/sw/php/current/lib/php/doc/Structures_Graph/docs/html/Structures_Graph/_Structures_Graph_Manipulator_AcyclicTest_php.html
/data00/sw/php/current/lib/php/doc/Structures_Graph/docs/html/Structures_Graph/Structures_Graph_Node.html
/data00/sw/php/current/lib/php/doc/Structures_Graph/docs/html/Structures_Graph/_Structures_Graph_php.html
/data00/sw/php/current/lib/php/doc/Structures_Graph/docs/html/Structures_Graph/Structures_Graph.html
/data00/sw/php/current/lib/php/doc/Structures_Graph/docs/html/Structures_Graph/tutorial_Structures_Graph.pkg.html
/data00/sw/php/current/lib/php/doc/Structures_Graph/docs/html/Structures_Graph/_Structures_Graph_Manipulator_TopologicalSorter_php.html
/data00/sw/php/current/lib/php/doc/Structures_Graph/docs/html/li_Structures_Graph.html
/data00/sw/php/current/lib/php/doc/Structures_Graph/docs/html/packages.html
/data00/sw/php/current/lib/php/doc/Structures_Graph/docs/html/errors.html
/data00/sw/php/current/lib/php/doc/Structures_Graph/docs/generate.sh
/data00/sw/php/current/lib/php/doc/Structures_Graph/docs/tutorials
/data00/sw/php/current/lib/php/doc/Structures_Graph/docs/tutorials/Structures_Graph
/data00/sw/php/current/lib/php/doc/Structures_Graph/docs/tutorials/Structures_Graph/Structures_Graph.pkg
/data00/sw/php/current/lib/php/doc/HTML_Template_IT
/data00/sw/php/current/lib/php/doc/HTML_Template_IT/LICENSE
/data00/sw/php/current/lib/php/doc/HTML_Template_IT/examples
/data00/sw/php/current/lib/php/doc/HTML_Template_IT/examples/sample_itx_addblockfile.php
/data00/sw/php/current/lib/php/doc/HTML_Template_IT/examples/sample_it.php
/data00/sw/php/current/lib/php/doc/HTML_Template_IT/examples/templates
/data00/sw/php/current/lib/php/doc/HTML_Template_IT/examples/templates/main.tpl.htm
/data00/sw/php/current/lib/php/doc/HTML_Template_IT/examples/templates/addblockfile_list.tpl.htm
/data00/sw/php/current/lib/php/doc/HTML_Template_IT/examples/templates/addblockfile_main.tpl.htm
/data00/sw/php/current/lib/php/doc/PEAR_Info
/data00/sw/php/current/lib/php/doc/PEAR_Info/examples
/data00/sw/php/current/lib/php/doc/PEAR_Info/examples/pear_info6.php
/data00/sw/php/current/lib/php/doc/PEAR_Info/examples/pear_info2.php
/data00/sw/php/current/lib/php/doc/PEAR_Info/examples/pear_info7.php
/data00/sw/php/current/lib/php/doc/PEAR_Info/examples/blueskin.css
/data00/sw/php/current/lib/php/doc/PEAR_Info/examples/pearinfo3.css
/data00/sw/php/current/lib/php/doc/PEAR_Info/examples/pear_info3.php
/data00/sw/php/current/lib/php/doc/PEAR_Info/examples/pear_info5.php
/data00/sw/php/current/lib/php/doc/PEAR_Info/examples/pear_info4.php
/data00/sw/php/current/lib/php/doc/PEAR_Info/examples/pear_info.php
/data00/sw/php/current/lib/php/doc/Archive_Tar
/data00/sw/php/current/lib/php/doc/Archive_Tar/docs
/data00/sw/php/current/lib/php/doc/Archive_Tar/docs/Archive_Tar.txt
/data00/sw/php/current/lib/php/.depdb
/data00/sw/php/current/lib/php/.lock
/data00/sw/php/current/lib/php/Structures
/data00/sw/php/current/lib/php/Structures/Graph
/data00/sw/php/current/lib/php/Structures/Graph/Manipulator
/data00/sw/php/current/lib/php/Structures/Graph/Manipulator/AcyclicTest.php
/data00/sw/php/current/lib/php/Structures/Graph/Manipulator/TopologicalSorter.php
/data00/sw/php/current/lib/php/Structures/Graph/Node.php
/data00/sw/php/current/lib/php/Structures/Graph.php
/data00/sw/php/current/lib/php/test
/data00/sw/php/current/lib/php/test/XML_Util
/data00/sw/php/current/lib/php/test/XML_Util/tests
/data00/sw/php/current/lib/php/test/XML_Util/tests/testBug_5392.phpt
/data00/sw/php/current/lib/php/test/XML_Util/tests/testBug_4950.phpt
/data00/sw/php/current/lib/php/test/XML_Util/tests/testBasic_apiVersion.phpt
/data00/sw/php/current/lib/php/test/XML_Util/tests/testBasic_splitQualifiedName.phpt
/data00/sw/php/current/lib/php/test/XML_Util/tests/testBasic_replaceEntities.phpt
/data00/sw/php/current/lib/php/test/XML_Util/tests/testBasic_getDocTypeDeclaration.phpt
/data00/sw/php/current/lib/php/test/XML_Util/tests/testBasic_createTagFromArray.phpt
/data00/sw/php/current/lib/php/test/XML_Util/tests/testBasic_collapseEmptyTags.phpt
/data00/sw/php/current/lib/php/test/XML_Util/tests/AllTests.php
/data00/sw/php/current/lib/php/test/XML_Util/tests/testBasic_attributesToString.phpt
/data00/sw/php/current/lib/php/test/XML_Util/tests/testBasic_createStartElement.phpt
/data00/sw/php/current/lib/php/test/XML_Util/tests/testBasic_createCDataSection.phpt
/data00/sw/php/current/lib/php/test/XML_Util/tests/testBasic_isValidName.phpt
/data00/sw/php/current/lib/php/test/XML_Util/tests/testBasic_reverseEntities.phpt
/data00/sw/php/current/lib/php/test/XML_Util/tests/testBasic_raiseError.phpt
/data00/sw/php/current/lib/php/test/XML_Util/tests/testBasic_getXmlDeclaration.phpt
/data00/sw/php/current/lib/php/test/XML_Util/tests/testBasic_createEndElement.phpt
/data00/sw/php/current/lib/php/test/XML_Util/tests/testBasic_createTag.phpt
/data00/sw/php/current/lib/php/test/XML_Util/tests/testBasic_createComment.phpt
/data00/sw/php/current/lib/php/test/Console_Getargs
/data00/sw/php/current/lib/php/test/Console_Getargs/tests
/data00/sw/php/current/lib/php/test/Console_Getargs/tests/AllTests.php
/data00/sw/php/current/lib/php/test/Console_Getargs/tests/Getargs_getValues_testcase.php
/data00/sw/php/current/lib/php/test/Console_Getargs/tests/Getargs_basic_testcase.php
/data00/sw/php/current/lib/php/test/Structures_Graph
/data00/sw/php/current/lib/php/test/Structures_Graph/tests
/data00/sw/php/current/lib/php/test/Structures_Graph/tests/AllTests.php
/data00/sw/php/current/lib/php/test/Structures_Graph/tests/testCase
/data00/sw/php/current/lib/php/test/Structures_Graph/tests/testCase/BasicGraph.php
/data00/sw/php/current/lib/php/test/HTML_Template_IT
/data00/sw/php/current/lib/php/test/HTML_Template_IT/tests
/data00/sw/php/current/lib/php/test/HTML_Template_IT/tests/ITTest.php
/data00/sw/php/current/lib/php/test/HTML_Template_IT/tests/ITXTest.php
/data00/sw/php/current/lib/php/test/HTML_Template_IT/tests/AllTests.php
/data00/sw/php/current/lib/php/test/HTML_Template_IT/tests/templates
/data00/sw/php/current/lib/php/test/HTML_Template_IT/tests/templates/__include.html
/data00/sw/php/current/lib/php/test/HTML_Template_IT/tests/templates/loadtemplatefile.html
/data00/sw/php/current/lib/php/test/HTML_Template_IT/tests/templates/replaceblock.html
/data00/sw/php/current/lib/php/test/HTML_Template_IT/tests/templates/bug_9853_01.tpl
/data00/sw/php/current/lib/php/test/HTML_Template_IT/tests/templates/globals.html
/data00/sw/php/current/lib/php/test/HTML_Template_IT/tests/templates/blocks.html
/data00/sw/php/current/lib/php/test/HTML_Template_IT/tests/templates/bug_9853_02.tpl
/data00/sw/php/current/lib/php/test/HTML_Template_IT/tests/templates/include.html
/data00/sw/php/current/lib/php/test/HTML_Template_IT/tests/templates/placeholderreplacementscope.html
/data00/sw/php/current/lib/php/test/HTML_Template_IT/tests/templates/blockiteration.html
/data00/sw/php/current/lib/php/test/HTML_Template_IT/tests/templates/addblock.html
/data00/sw/php/current/lib/php/test/PEAR_Info
/data00/sw/php/current/lib/php/test/PEAR_Info/tests
/data00/sw/php/current/lib/php/test/PEAR_Info/tests/PEAR_Info_TestSuite_Standard.php
/data00/sw/php/current/lib/php/test/PEAR_Info/tests/render.phpt
/data00/sw/php/current/lib/php/test/PEAR_Info/tests/sysconf_dir
/data00/sw/php/current/lib/php/test/PEAR_Info/tests/sysconf_dir/empty_dir.txt
/data00/sw/php/current/lib/php/test/PEAR_Info/tests/install.phpt
/data00/sw/php/current/lib/php/test/PEAR_Info/tests/user_dir
/data00/sw/php/current/lib/php/test/PEAR_Info/tests/user_dir/empty_dir.txt
/data00/sw/php/current/lib/php/test/PEAR_Info/tests/pear_dir
/data00/sw/php/current/lib/php/test/PEAR_Info/tests/pear_dir/.channels
/data00/sw/php/current/lib/php/test/PEAR_Info/tests/pear_dir/.channels/.alias
/data00/sw/php/current/lib/php/test/PEAR_Info/tests/pear_dir/.channels/.alias/pear.txt
/data00/sw/php/current/lib/php/test/PEAR_Info/tests/pear_dir/.channels/.alias/pecl.txt
/data00/sw/php/current/lib/php/test/PEAR_Info/tests/pear_dir/.channels/.alias/phpunit.txt
/data00/sw/php/current/lib/php/test/PEAR_Info/tests/pear_dir/.channels/pear.phpunit.de.reg
/data00/sw/php/current/lib/php/test/PEAR_Info/tests/pear_dir/.channels/pecl.php.net.reg
/data00/sw/php/current/lib/php/test/PEAR_Info/tests/pear_dir/.channels/pear.php.net.reg
/data00/sw/php/current/lib/php/test/PEAR_Info/tests/pear_dir/.channels/__uri.reg
/data00/sw/php/current/lib/php/test/PEAR_Info/tests/pear_dir/.registry
/data00/sw/php/current/lib/php/test/PEAR_Info/tests/pear_dir/.registry/pear.reg
/data00/sw/php/current/lib/php/test/PEAR_Info/tests/pear_dir/.registry/console_getopt.reg
/data00/sw/php/current/lib/php/test/PEAR_Info/tests/pear_dir/.registry/.channel.__uri
/data00/sw/php/current/lib/php/test/PEAR_Info/tests/pear_dir/.registry/.channel.__uri/empty_dir.txt
/data00/sw/php/current/lib/php/test/PEAR_Info/tests/pear_dir/.registry/text_diff.reg
/data00/sw/php/current/lib/php/test/PEAR_Info/tests/pear_dir/.registry/.channel.pear.phpunit.de
/data00/sw/php/current/lib/php/test/PEAR_Info/tests/pear_dir/.registry/.channel.pear.phpunit.de/phpunit.reg
/data00/sw/php/current/lib/php/test/PEAR_Info/tests/pear_dir/.registry/.channel.pecl.php.net
/data00/sw/php/current/lib/php/test/PEAR_Info/tests/pear_dir/.registry/.channel.pecl.php.net/empty_dir.txt
/data00/sw/php/current/lib/php/test/PEAR_Info/tests/AllTests.php
/data00/sw/php/current/lib/php/test/PEAR_Info/tests/templates
/data00/sw/php/current/lib/php/test/PEAR_Info/tests/templates/blueskin.css
/data00/sw/php/current/lib/php/test/PEAR_Info/tests/templates/packages.tpl
/data00/sw/php/current/lib/php/test/PEAR_Info/tests/templates/general.tpl
/data00/sw/php/current/lib/php/test/PEAR_Info/tests/templates/credits.tpl
/data00/sw/php/current/lib/php/test/PEAR_Info/tests/customConfig.phpt
/data00/sw/php/current/lib/php/test/PEAR_Info/tests/pear2_dir
/data00/sw/php/current/lib/php/test/PEAR_Info/tests/pear2_dir/empty_dir.txt
/data00/sw/php/current/lib/php/test/PEAR_Info/tests/defaultConfig.phpt
/data00/sw/php/current/lib/php/XML
/data00/sw/php/current/lib/php/XML/Util.php
/data00/sw/php/current/lib/php/PEAR5.php
/data00/sw/php/current/lib/php/.channels
/data00/sw/php/current/lib/php/.channels/.alias
/data00/sw/php/current/lib/php/.channels/.alias/phpdocs.txt
/data00/sw/php/current/lib/php/.channels/.alias/pear.txt
/data00/sw/php/current/lib/php/.channels/.alias/pecl.txt
/data00/sw/php/current/lib/php/.channels/pecl.php.net.reg
/data00/sw/php/current/lib/php/.channels/pear.php.net.reg
/data00/sw/php/current/lib/php/.channels/doc.php.net.reg
/data00/sw/php/current/lib/php/.channels/__uri.reg
/data00/sw/php/current/lib/php/.registry
/data00/sw/php/current/lib/php/.registry/pear.reg
/data00/sw/php/current/lib/php/.registry/.channel.doc.php.net
/data00/sw/php/current/lib/php/.registry/console_getopt.reg
/data00/sw/php/current/lib/php/.registry/archive_tar.reg
/data00/sw/php/current/lib/php/.registry/.channel.__uri
/data00/sw/php/current/lib/php/.registry/console_getargs.reg
/data00/sw/php/current/lib/php/.registry/pear_info.reg
/data00/sw/php/current/lib/php/.registry/.channel.pecl.php.net
/data00/sw/php/current/lib/php/.registry/structures_graph.reg
/data00/sw/php/current/lib/php/.registry/xml_util.reg
/data00/sw/php/current/lib/php/.registry/html_template_it.reg
/data00/sw/php/current/lib/php/pearcmd.php
/data00/sw/php/current/lib/php/PEAR.php
/data00/sw/php/current/lib/php/Archive
/data00/sw/php/current/lib/php/Archive/Tar.php
/data00/sw/php/current/lib/php.ini


pear config-show:
Configuration (channel pear.php.net):
=====================================
Auto-discover new Channels     auto_discover    <not set>
Default Channel                default_channel  pear.php.net
HTTP Proxy Server Address      http_proxy       http://<myhostname>:3128
PEAR server [DEPRECATED]       master_server    pear.php.net
Default Channel Mirror         preferred_mirror pear.php.net
Remote Configuration File      remote_config    <not set>
PEAR executables directory     bin_dir          /data00/sw/php/5.2.15/bin
PEAR documentation directory   doc_dir          /data00/sw/php/5.2.15/lib/php/doc
PHP extension directory        ext_dir          /data00/sw/php/5.2.15/lib/php/extensions/no-debug-non-zts-20060613
PEAR directory                 php_dir          /data00/sw/php/5.2.15/lib/php
PEAR Installer cache directory cache_dir        /tmp/pear/cache
PEAR configuration file        cfg_dir          /data00/sw/php/5.2.15/lib/php/cfg
directory
PEAR data directory            data_dir         /data00/sw/php/5.2.15/lib/php/data
PEAR Installer download        download_dir     /tmp/pear/download
directory
PHP CLI/CGI binary             php_bin          /data00/sw/php/5.2.15/bin/php
php.ini location               php_ini          /data00/sw/php/current/lib/php.ini
--program-prefix passed to     php_prefix       <not set>
PHP's ./configure
--program-suffix passed to     php_suffix       <not set>
PHP's ./configure
PEAR Installer temp directory  temp_dir         /tmp/pear/temp
PEAR test directory            test_dir         /data00/sw/php/5.2.15/lib/php/test
PEAR www files directory       www_dir          /data00/sw/php/5.2.15/lib/php/htdocs
Cache TimeToLive               cache_ttl        3600
Preferred Package State        preferred_state  stable
Unix file mask                 umask            77
Debug Log Level                verbose          1
PEAR password (for             password         <not set>
maintainers)
Signature Handling Program     sig_bin          /usr/bin/gpg
Signature Key Directory        sig_keydir       /data00/sw/php/5.2.15/etc/pearkeys
Signature Key Id               sig_keyid        <not set>
Package Signature Type         sig_type         gpg
PEAR username (for             username         <not set>
maintainers)
User Configuration File        Filename         /home/anlocal/.pearrc
System Configuration File      Filename         /data00/sw/php/5.2.15/etc/pear.conf


phpinfo.php

System	Linux <myhostname> 2.6.18-194.17.1.el5 #1 SMP Mon Sep 20 07:12:06 EDT 2010 x86_64
Build Date	Dec 16 2010 07:54:45
Configure Command	 './configure' '--prefix=/data00/sw/php/5.2.15' '--with-mysql' '--with-libdir=lib64' '--with-apxs2=/data00/sw/apache/current/bin/apxs' '--enable-sockets' '--with-ldap' '--with-gettext'
Server API	Apache 2.0 Handler
Virtual Directory Support	disabled
Configuration File (php.ini) Path	/data00/sw/php/5.2.15/lib
Loaded Configuration File	/data0/sw/php/5.2.15/lib/php.ini
Scan this dir for additional .ini files	(none)
additional .ini files parsed	(none)
PHP API	20041225
PHP Extension	20060613
Zend Extension	220060519
Debug Build	no
Thread Safety	disabled
Zend Memory Manager	enabled
IPv6 Support	enabled
Registered PHP Streams	php, file, data, http, ftp
Registered Stream Socket Transports	tcp, udp, unix, udg
Registered Stream Filters	convert.iconv.*, string.rot13, string.toupper, string.tolower, string.strip_tags, convert.*, consumed



Honestly have no idea where to go....

Please help folks! :(

Aaron.

---

### Post by STOIE on 2010-12-20
Bump!

---

