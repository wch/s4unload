Test packages with S4 unload warnings
=====================================

There are three packages here, one of which results in warnings when unloaded.

* s4i: The NAMESPACE file has `import(methods)`
* s4c: The class TestClass has `contains = "lm"`
* s4ic: The NAMESPACE file has `import(methods)` and the class TestClass has `contains = "lm"`

The last one, `s4ic` gives warnings when unloaded. To replicate:


```
install.packages(c('s4i', 's4c', 's4ic'), repos=NULL, type='source')

library(s4i)
unloadNamespace('s4i')
# OK

library(s4c)
unloadNamespace('s4c')
# OK

library(s4ic)
unloadNamespace('s4ic')
# 1: In FUN(X[[2L]], ...) :
#   Created a package name, ‘2013-12-19 12:08:51’, when none found
# 2: In FUN(X[[2L]], ...) :
#   Created a package name, ‘2013-12-19 12:08:51’, when none found
```
