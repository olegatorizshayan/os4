# os4 (Zadorozhnyi 8)

# Синтаксис
NAME
       rmdir - remove empty directories

SYNOPSIS
       rmdir [OPTION]... DIRECTORY...

DESCRIPTION
       Remove the DIRECTORY(ies), if they are empty.

       --ignore-fail-on-non-empty

              ignore each failure that is solely because a directory

              is non-empty

       -p, --parents
              remove  DIRECTORY  and  its ancestors; e.g., 'rmdir -p a/b/c' is
              similar to 'rmdir a/b/c a/b a'

       -v, --verbose
              output a diagnostic for every directory processed

       --help display this help and exit

       --version
              output version information and exit

AUTHOR
       Written by David MacKenzie.

# Code
#include <unistd.h>

#include <stdio.h>

int main(int argc, char* argv[]) {

    int s = rmdir(argv[1]);
    if(s != -1) {
        printf("%s",argv[1]);
        printf(" removed\n");
        return 0;
    }
    printf("%s",argv[1]);
    printf(" not removed!\n");
    return -1;
}


# compile

gcc main.c

# run

./a.out <dir_name>

# good example

bodhi@bodhi-MacBookAir:~/OS4$ mkdir Maks-krutoi

bodhi@bodhi-MacBookAir:~/OS4$ ./a.out Maks-krutoi/

Maks-krutoi/ removed

# bad example

bodhi@bodhi-MacBookAir:~/OS4$ ls

a.out  main.c

bodhi@bodhi-MacBookAir:~/OS4$ ./a.out Maks-krutoi

Maks-krutoi not removed!
