# Environment Switcher

* Author: `Adam Bolte`_
* Contact: adam.bolte@sitepoint.com
* Copyright: `GPL3+`_

## Usage
```shell
$ cat ~/.bashrc
eval "$(envswitch -i)"

$ cat ~/.config/envswitch/random.conf
randomvar=$RANDOM
$ cat ~/.config/envswitch/depend.conf
dependvar="dependon$randomvar"
$ cat ~/.config/envswitch/random.conf
anothervar1=value1
anothervar2=value2

$ envswitch -l
another
depend
random

$ random
Loading profile: random
Setting randomvar=$RANDOM

(random) $ depend
Loading profile: depend
Setting dependvar="dependon$randomvar"

(depend) (random) $ another
Loading profile: another
Setting anothervar1=value1
Setting anothervar2=value2

(another) (depend) (random) $ export
eclare -x anothervar1="value1"
declare -x anothervar2="value2"
declare -x dependvar="dependon5072"
declare -x randomvar="5072"

(another) (depend) (random) $ envswitch -s
Profile: another
anothervar1=value1
anothervar2=value2
Profile: depend
dependvar="dependon$randomvar"
Profile: random
randomvar=$RANDOM

(another) (depend) (random) $ envreset
Resetting environments: another depend random
Resetting profile: another
Unsetting anothervar1
Unsetting anothervar2
Resetting profile: depend
Unsetting dependvar
Resetting profile: random
Unsetting randomvar

$ envswitch -s
No environment loaded.
```
