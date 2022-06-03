# Group Members

```bash
Name                     ID
1. Eliyas Asefa          ETS 0346/11
2. Daniel Shobbe         ETS 0286/11
3. Abdurahman Mohammed   ETS 0016/11
4. Muhammed Aman         ETS 0063/10
5. Fikir Mekonnin        ETS 0435/11
6. Bezawit Girma         ETS 0206/11
```
# Bitmap

A bitmap is a data structure that implements an array of booleans in a very
memory efficient way; though the time complexity of this implementation
isn't constant, given the fact cpu registers will store the same bytes in
them for a prolonged period of time with accesses restricted to the
same memory region, this data structure often outperforms others with
better time complexity.

# API

```c
typedef struct _bm {
    uint8_t *bits;
    size_t max_index;
} Bitmap_t;

extern void Bitmap_init(Bitmap_t *bm, size_t sz);
extern uint8_t Bitmap_at(Bitmap_t *bm, size_t index);
extern void Bitmap_set(Bitmap_t *bm, size_t index, uint8_t set_bit);
extern void Bitmap_free(Bitmap_t *bm);
```
# Instructions 
Step 1:
```bash
make
```
Step 2: 
```
./bin/test [number of bytes you want to allocate]
``` 
For example:  
```
./bin/test 1000
```
(Optional) Step 3 [to deallocate memory]: 
```
./bin/test2
``` 
# Example usage

```c
#include <stdio.h>
#include <bitmap.h>

int main(void)
{
    Bitmap_t bm;

    /* initialize bitmap with 8 spaces */
    Bitmap_init(&bm, 8);

    /* set the first bit */
    Bitmap_set(&bm, 0, 1);

    /* set the third bit */
    Bitmap_set(&bm, 2, 1);

    /* set the last bit */
    Bitmap_set(&bm, 7, 1);

    /* print set bits */
    for (int i = 0; i < 8; i++)
        putchar((Bitmap_at(&bm, i)) ? '1' : '0');

    putchar('\n');

    /* free the allocated space in memory */
    Bitmap_free(&bm);

    return 0;
}
```
