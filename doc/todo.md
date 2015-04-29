"to do" list
===

Short-term
---

* stree: In addition to the callback, add an iterator for traversal.
* stree: min, max, range query, iterator.
* copy behavior: cut on size limit (stack storage and size_t limits)
* size/len incoherences (e.g. get_len / get_size)
* adjust size: string structure is not properly used.
* add overflow checks, using "s_size_t_overflow"
* Make last-inserted nodes cache, in order to speed-up delete.
* Add st_shl and st_shr for shifting elements on a vector.
* Example: RGB888 to palette
* sstring renaming/cleanup (e.g. ss_dup_s -> ss_dup, *_shrink_to_fit -> *_shrink, replace -> replaceall), add tests for the stack allocation limits.
* Write examples

Mid-term
---

* String enhancements
 * Search multiple targets on string keeping with O(m * n) worst search time (not O(n^2), but cheap one-pass)
 * Cache Rabin-Karpin hashes for amortized cost when repeating search with same target ("needle").
 * Add SSE 4.2 SIMD intrinsics for increasing from 1GB/s up to the saturation of the memory bus (e.g. 10GB/s per core at 3GHz) \-not 100% sure if that much will be possible, but I have some ideas\-
 * Quote strings (e.g. like in sds)
 * String analysis (naive Bayes, weight/entropy)
 * Check if some important string functionality is missing.
 * Unicode: to_lower, to_title, fold_case and normalize. http://www.boost.org/doc/libs/1_51_0/libs/locale/doc/html/conversions.html http://en.wikipedia.org/wiki/Capitalization http://ftp.unicode.org/Public/UNIDATA/CaseFolding.txt
* Tree enhancements
* Other
 * Bindings for other languages
* Add some simple data compression (e.g. 4KB LZW or 32KB LZ77 + Huffman coding)

Long-term (never)
---

* Time/date
* C++ wrapper
* Add UTF8 regexp support

QA
===

Short-term
---

* more synthetic description, simplify it (avoid unnecesary detail)
* review function per functtion.
* write readme.md and documentation (manual pages, Doxygen)
* Ensure: if can not no realloc memory, string is kept untouched.
* List C library dependencies

Mid-term
---

* Tests
 * ADD tests for every operation related to unicode caching.
 *  Check case unicode size (add tests: e.g. erasing with overflow, etc.)
 * aliasing: stack, lower/middle/upper case checks, etc.
 * sstring accessors (ss_get_buffer, ...)
 * tests using stack space
 * add tests covering expansion between small/medium/full strings
 * add checks for all corner cases (!)
 * reentrancy: 1) write size afterwards, 2) in case of buffer switch, point those cases in the "behavior" section.
