CREATE TABLE `invoicemaster` (
	`id` INT(11) NOT NULL AUTO_INCREMENT,
	`invoice_no` INT(10) NOT NULL,
	`client_id` INT(10) NOT NULL,
	`invoice_date` DATE NOT NULL,
	`total_amount` DECIMAL(15,2) NOT NULL,
	`CreatedAt` TIMESTAMP NOT NULL DEFAULT current_timestamp(),
	PRIMARY KEY (`id`) USING BTREE,
	UNIQUE INDEX `invoice_no` (`invoice_no`) USING BTREE,
	INDEX `client_id` (`client_id`) USING BTREE,
	CONSTRAINT `invoicemaster_ibfk_1` FOREIGN KEY (`client_id`) REFERENCES `clientmaster` (`id`) ON UPDATE RESTRICT ON DELETE RESTRICT
)
COLLATE='utf8mb4_general_ci'
ENGINE=InnoDB
AUTO_INCREMENT=24
;



CREATE TABLE `invoicedetails` (
	`invoice_id` INT(10) NOT NULL,
	`item_id` INT(10) NOT NULL,
	`quantity` INT(10) NOT NULL,
	`price` DECIMAL(10,2) NOT NULL,
	`total_price` DECIMAL(15,2) NOT NULL,
	INDEX `invoice_id` (`invoice_id`) USING BTREE,
	INDEX `item_id` (`item_id`) USING BTREE,
	CONSTRAINT `invoicedetails_ibfk_1` FOREIGN KEY (`invoice_id`) REFERENCES `invoicemaster` (`id`) ON UPDATE RESTRICT ON DELETE CASCADE,
	CONSTRAINT `invoicedetails_ibfk_2` FOREIGN KEY (`item_id`) REFERENCES `itemmaster` (`id`) ON UPDATE RESTRICT ON DELETE RESTRICT
)
COLLATE='utf8mb4_general_ci'
ENGINE=InnoDB
;
