# JS-practice

/**
 * Custom implementation of the Array.prototype.map() method.
 * Creates a new array populated with the results of calling a provided function
 * on every element in the calling array.
 *
 * @param {Array} arr - The input array to iterate over.
 * @param {Function} callback - A function that is called for every element in the array.
 * It takes three arguments:
 * - currentValue: The current element being processed in the array.
 * - index: The index of the current element being processed in the array.
 * - array: The array map was called upon.
 * @returns {Array} A new array with each element being the result of the callback function.

 */
###
 
      export function myMap(arr, callback) {
        // Check if the input is an array and the callback is a function
        if (!Array.isArray(arr)) {
          console.error("myMap: First argument must be an array.");
          return [];
        }
        if (typeof callback !== 'function') {
          console.error("myMap: Second argument must be a function.");
          return [];
        }
      
        const result = [];
        for (let i = 0; i < arr.length; i++) {
          // Call the callback function with (currentValue, index, array)
          result.push(callback(arr[i], i, arr));
        }
        return result;
      }
###
/**
 * Custom implementation of the Array.prototype.filter() method.
 * Creates a new array with all elements that pass the test implemented by the provided function.
 *
 * @param {Array} arr - The input array to iterate over.
 * @param {Function} callback - A function that is called for every element in the array.
 * It takes three arguments:
 * - currentValue: The current element being processed in the array.
 * - index: The index of the current element being processed in the array.
 * - array: The array filter was called upon.
 * It should return a truthy value to keep the element, or a falsy value otherwise.
 * @returns {Array} A new array with the elements that pass the test.

 */
 ###
       
      export function myFilter(arr, callback) {
        // Check if the input is an array and the callback is a function
        if (!Array.isArray(arr)) {
          console.error("myFilter: First argument must be an array.");
          return [];
        }
        if (typeof callback !== 'function') {
          console.error("myFilter: Second argument must be a function.");
          return [];
        }
      
        const result = [];
        for (let i = 0; i < arr.length; i++) {
          // Call the callback function with (currentValue, index, array)
          // If the callback returns true, add the element to the result array
          if (callback(arr[i], i, arr)) {
            result.push(arr[i]);
          }
        }
        return result;
      }
###
/**
 * Custom implementation of the Array.prototype.reduce() method.
 * Executes a reducer function (that you provide) on each element of the array,
 * resulting in a single output value.
 *
 * @param {Array} arr - The input array to iterate over.
 * @param {Function} callback - A reducer function that is called for every element in the array.
 * It takes four arguments:
 * - accumulator: The accumulated value previously returned in the last invocation
 * of the callback, or the initialValue, or the first element of the array.
 * - currentValue: The current element being processed in the array.
 * - index: The index of the current element being processed in the array.
 * - array: The array reduce was called upon.
 * @param {*} [initialValue] - An optional value to use as the first argument to the first call of the callback.
 * If no initialValue is supplied, the first element in the array will be used as the initial accumulator value
 * and currentValue will start with the second element.
 * @returns {*} The single value that results from the reduction.

 */

 ###
       
      export function myReduce(arr, callback, initialValue) {
        // Check if the input is an array and the callback is a function
        if (!Array.isArray(arr)) {
          console.error("myReduce: First argument must be an array.");
          return undefined; // Or throw an error, depending on desired behavior
        }
        if (typeof callback !== 'function') {
          console.error("myReduce: Second argument must be a function.");
          return undefined;
        }
      
        const hasInitialValue = arguments.length >= 3;
        let accumulator = hasInitialValue ? initialValue : arr[0];
        let startIndex = hasInitialValue ? 0 : 1;
      
        // If no initialValue is provided and the array is empty, throw an error
        if (!hasInitialValue && arr.length === 0) {
          throw new TypeError('Reduce of empty array with no initial value');
        }
        // If no initialValue is provided and the array has only one element, return that element
        if (!hasInitialValue && arr.length === 1) {
          return arr[0];
        }
      
      
        for (let i = startIndex; i < arr.length; i++) {
          // Call the callback function with (accumulator, currentValue, index, array)
          accumulator = callback(accumulator, arr[i], i, arr);
        }
      
        return accumulator;
      }
###
