/*

Procedure for bulk insert data: Load Bronze Layer (Source -> Bronze)

*/

CREATE OR ALTER PROCEDURE bronze.load_bronze as 
BEGIN
	DECLARE @start_time DATETIME, @end_time DATETIME, @start_whole DATETIME, @end_whole DATETIME;
	BEGIN TRY
		
		SET @start_whole = GETDATE(); 

		PRINT '=======================================';
		PRINT 'Loading Bronze Layer';
		PRINT '=======================================';


		PRINT '---------------------------------------';
		PRINT ' Loading CRM TABLEs';
		PRINT '---------------------------------------';

		SET @start_time = GETDATE();

		PRINT '>> Truncating TABLE: bronze.crm_cust_info';
		TRUNCATE TABLE bronze.crm_cust_info;
		PRINT '>> Inserting Data Into TABLE: bronze.crm_cust_info';
		BULK INSERT bronze.crm_cust_info
		FROM 'C:\Users\szamo\Desktop\SQL\Data Warehouse Project\sql-data-warehouse-project\datasets\source_crm\cust_info.csv'
		WITH(
			FIRSTROW = 2,
			FIELDTERMINATOR = ',',
			TABLOCK
		);

		SET @end_time = GETDATE();
		PRINT '>> Load Duration: ' + CAST(DATEDIFF(millisecond, @start_time, @end_time) as NVARCHAR(50)) + ' milliseconds';
		PRINT '>> ----------------';

		SET @start_time = GETDATE();
		PRINT '>> Truncating TABLE: bronze.crm_prd_info';
		TRUNCATE TABLE bronze.crm_prd_info;
		PRINT '>> Inserting Data Into TABLE: bronze.crm_prd_info';
		BULK INSERT bronze.crm_prd_info
		FROM 'C:\Users\szamo\Desktop\SQL\Data Warehouse Project\sql-data-warehouse-project\datasets\source_crm\prd_info.csv'
		WITH(
			FIRSTROW = 2,
			FIELDTERMINATOR = ',',
			TABLOCK
		);

		SET @end_time = GETDATE();
		PRINT '>> Load Duration: ' + CAST(DATEDIFF(millisecond, @start_time, @end_time) as NVARCHAR(50)) + ' milliseconds';
		PRINT '>> ----------------';

		SET @start_time = GETDATE();
		PRINT '>> Truncating TABLE: bronze.crm_sales_details';
		TRUNCATE TABLE bronze.crm_sales_details;
		PRINT '>> Inserting Data Into TABLE: bronze.crm_sales_details';
		BULK INSERT bronze.crm_sales_details
		FROM 'C:\Users\szamo\Desktop\SQL\Data Warehouse Project\sql-data-warehouse-project\datasets\source_crm\sales_details.csv'
		WITH(
			FIRSTROW = 2,
			FIELDTERMINATOR = ',',
			TABLOCK
		);

		SET @end_time = GETDATE();
		PRINT '>> Load Duration: ' + CAST(DATEDIFF(millisecond, @start_time, @end_time) as NVARCHAR(50)) + ' milliseconds';
		PRINT '>> ----------------';

		PRINT '---------------------------------------';
		PRINT ' Loading ERP TABLEs';
		PRINT '---------------------------------------';

		SET @start_time = GETDATE();

		PRINT '>> Truncating TABLE: bronze.erp_cust_az12';
		TRUNCATE TABLE bronze.erp_cust_az12;
		PRINT '>> Inserting Data Into TABLE: bronze.erp_cust_az12';
		BULK INSERT bronze.erp_cust_az12
		FROM 'C:\Users\szamo\Desktop\SQL\Data Warehouse Project\sql-data-warehouse-project\datasets\source_erp\cust_az12.csv'
		WITH(
			FIRSTROW = 2,
			FIELDTERMINATOR = ',',
			TABLOCK
		);

		SET @end_time = GETDATE();
		PRINT '>> Load Duration: ' + CAST(DATEDIFF(millisecond, @start_time, @end_time) as NVARCHAR(50)) + ' milliseconds';
		PRINT '>> ----------------';

		SET @start_time = GETDATE();

		PRINT '>> Truncating TABLE: bronze.erp_loc_a101';
		TRUNCATE TABLE bronze.erp_loc_a101;
		PRINT '>> Inserting Data Into TABLE: bronze.erp_loc_a101';
		BULK INSERT bronze.erp_loc_a101
		FROM 'C:\Users\szamo\Desktop\SQL\Data Warehouse Project\sql-data-warehouse-project\datasets\source_erp\loc_a101.csv'
		WITH(
			FIRSTROW = 2,
			FIELDTERMINATOR = ',',
			TABLOCK
		);

		SET @end_time = GETDATE();
		PRINT '>> Load Duration: ' + CAST(DATEDIFF(millisecond, @start_time, @end_time) as NVARCHAR(50)) + ' milliseconds';
		PRINT '>> ----------------';

		SET @start_time = GETDATE();

		PRINT '>> Truncating TABLE: bronze.erp_px_cat_g1v2';
		TRUNCATE TABLE bronze.erp_px_cat_g1v2;
		PRINT '>> Inserting Data Into TABLE: bronze.erp_px_cat_g1v2';
		BULK INSERT bronze.erp_px_cat_g1v2
		FROM 'C:\Users\szamo\Desktop\SQL\Data Warehouse Project\sql-data-warehouse-project\datasets\source_erp\px_cat_g1v2.csv'
		WITH(
			FIRSTROW = 2,
			FIELDTERMINATOR = ',',
			TABLOCK
		);

		SET @end_time = GETDATE();

		PRINT '>> Load Duration: ' + CAST(DATEDIFF(millisecond, @start_time, @end_time) as NVARCHAR(50)) + ' milliseconds';
		PRINT '>> ----------------';

		SET @end_whole = GETDATE(); 

		PRINT '==>> Load Duration Bronze Layer: ' + CAST(DATEDIFF(millisecond, @start_whole, @end_whole) as NVARCHAR(50)) + ' milliseconds';
		PRINT '==>> ----------------';

	END TRY
	BEGIN CATCH
		PRINT '===============================================';
		PRINT 'ERROR OCCURED DURING LOADING BRONZE LAYER';
		PRINT 'Error Message' + ERROR_MESSAGE();
		PRINT 'Error Message' + CAST(ERROR_NUMBER() AS NVARCHAR(50));
		PRINT 'Error Message' + CAST(ERROR_STATE() AS NVARCHAR(50));
		PRINT '===============================================';
	END CATCH
END;
