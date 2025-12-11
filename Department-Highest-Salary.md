select d.name as Department, e.name as Employee, e.salary as Salary from 
(select *, DENSE_RANK() OVER (PARTITION BY departmentId order by salary desc) as salar from employee) e 
join department d
 on e.departmentId = d.id 
where e.salar<=3 order by d.name,e.salary desc;
