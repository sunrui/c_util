# c_util
找到了 11 年前写过的一些用 c 的会指针装逼代码，怀念那些青涩的时光。

```
2011-9-4

void * my_memccpy(void *dest,const void *src,int c,int count)
{
    while ( count && (*((char *)(dest = (char *)dest + 1) - 1) =
        *((char *)(src = (char *)src + 1) - 1)) != (char)c )
        count--;
    return(count ? dest : NULL);

}

//memset
void *my_memset(void *buffer, int c, int count)
{
    char* p = (char*)buffer;
    while(count--) 
        *p++ = (char)c;
    return buffer;
}

//memcpy
void * my_memcpy(void *dst,const void *src,int count)
{
    void * ret = dst;
    while (count--) 
    {
        *(char *)dst = *(char *)src;
        dst = (char *)dst + 1;
        src = (char *)src + 1;
    }
    return(ret);
}

//memmove
/*
memmove()由src所指定的内存区域赋值count个字符到dst所指定的内存区域。
src和dst所指内存区域可以重叠，但复制后src的内容会被更改。函数返回指向dst的指针。
*/

void * my_memmove(void * dst,const void * src,int count)
{
    void * ret = dst;
    if (dst <= src || (char *)dst >= ((char *)src + count)) 
    {
        while (count--) 
        {
            *(char *)dst = *(char *)src;
            dst = (char *)dst + 1;
            src = (char *)src + 1;
        }
    }
    else 
    {
        dst = (char *)dst + count - 1;
        src = (char *)src + count - 1;
        while (count--) 
        {
            *(char *)dst = *(char *)src;
            dst = (char *)dst - 1;
            src = (char *)src - 1;
        }

    }
    return(ret);
}


char * __cdecl strcpy(char * dst, const char * src)
{
    char * cp = dst;
    while( *cp++ = *src++ )    ;         
    return( dst );
}

char * strcat (char * dst, char * src)
{
    char * cp = dst;
    while( *cp )
      ++cp;   /* Find end of dst */
    while( *cp++ = *src++ )
             /* Copy src to end of dst */
    return( dst );
}

int my_strlen(const char * str )
{
    const char *p = str;
    while( *p++ ) ;
    return( (int)(p - str - 1) );

}

//strcmp
int my_strcmp(const char *string1, const char *string2 )
{
    int ret;
    while(    ( ret=*(unsigned char *)string1++ -*(unsigned char *)string2++)==0 &&   string1  );
    return ret;
}
```
