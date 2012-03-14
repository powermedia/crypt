
    Erlang R13B03 (erts-5.7.4) [source] [rq:1] [async-threads:0] [hipe] [kernel-poll:false]
    
    Eshell V5.7.4  (abort with ^G)
    1> crypt:crypt("test","aa").
    "aaqPiZY5xR5l."
    2> crypt:crypt("test","$1$aaaaaaaa").
    "$1$aaaaaaaa$lWxWtPmiNjS/cwJnGm6fe0"
    3> crypt:crypt("test","$6$aaaaaaaa").
    "$6$aaaaaaaa$HREHv6TuSmUS/7spCDO5Js3ssSZ6.iwVkUoVtatJUhJDKVmERrRKBTolrPMub2s5dX6IEjZg6d6wZzFRlidV41"
    4> 

Which algorithms are supported by crypt are dependent on the system
crypt(3) library. For example, Mac OS X only supports DES (booooooo!!!!).


TODO
----

1. What is the maximum password and salt length?

   There doesn't appear to be a limit. DES has an 8 character limit and
   MD5 has a 256 character limit, but for the other types, no idea.

   sysconf(\_SC\_PASS\_MAX) seems to return the limit on Solaris, but isn't
   available on Ubuntu.

2. Provide an erlang version of the crypt() interface.

3. For systems that don't support MD5, maybe use openssl (see in openssl
   dist: apps/passwd.c).