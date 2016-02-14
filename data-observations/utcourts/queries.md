# Queries

To setup database, see README of https://github.com/s2t2/courtbot-slco/pull/1

Which court calendar .pdf documents have the greatest number of pages?

```` sql
SELECT
  court.id
  ,court.type
 ,court.name
 -- ,count(DISTINCT cals.id) AS calendar_count
  ,max(cals.pdf_created_at)::DATE AS pdf_created_on
 ,max(cals.page_count) AS pdf_page_count
  -- ,cals.pdf_modified_at
  -- ,cals.pdf_modified_at - cals.pdf_created_at AS modded
FROM utah_courts court
LEFT JOIN utah_court_calendars cals ON cals.utah_court_id = court.id
GROUP BY 1,2,3
ORDER BY 5 DESC
LIMIT 25
````

id | type | name | pdf_created_on | pdf_page_count
--- | --- | --- | --- | ---
29 | DistrictCourt | Salt Lake City | 2016-02-12 | 1062
123 | JusticeCourt | Salt Lake City | 2016-02-12 | 556
158 | JusticeCourt | West Valley City | 2016-02-12 | 429
25 | DistrictCourt | Provo | 2016-02-12 | 383
35 | DistrictCourt | West Jordan | 2016-02-12 | 301
157 | JusticeCourt | West Jordan | 2016-02-12 | 297
107 | JusticeCourt | Ogden City | 2016-02-12 | 279
8 | DistrictCourt | Farmington | 2016-02-12 | 278
152 | JusticeCourt | Washington County | 2016-02-12 | 269
143 | JusticeCourt | Taylorsville | 2016-02-12 | 262
22 | DistrictCourt | Ogden | 2016-02-12 | 255
148 | JusticeCourt | Utah County | 2016-02-12 | 250
32 | DistrictCourt | St. George | 2016-02-12 | 248
124 | JusticeCourt | Salt Lake County | 2016-02-12 | 199
116 | JusticeCourt | Provo | 2016-02-12 | 184
126 | JusticeCourt | Sandy | 2016-02-12 | 181
90 | JusticeCourt | Midvale | 2016-02-12 | 178
135 | JusticeCourt | South Salt Lake | 2016-02-12 | 172
98 | JusticeCourt | Murray City | 2016-02-12 | 169
109 | JusticeCourt | Orem City | 2016-02-12 | 156
1 | DistrictCourt | American Fork | 2016-02-12 | 134
144 | JusticeCourt | Tooele County | 2016-02-12 | 133
74 | JusticeCourt | Holladay | 2016-02-12 | 129
44 | JusticeCourt | Carbon County | 2016-02-12 | 123
15 | DistrictCourt | Logan | 2016-02-12 | 114
